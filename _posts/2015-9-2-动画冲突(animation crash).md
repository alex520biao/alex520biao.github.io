---
layout: post
title: 动画冲突
---


iOS开发时经常会出现动画冲突的情况，这是因为多个动画同一时间修改同一个视图元素，导致某些动画不能正常完成。这与多线程同时修改同一数据源导致异常的问题类似。

####一. 常见的动画冲突
动画A、动画B都是使用UIViewAnimate创建的动画，执行前将testViewA添加到self.view上,执行时长都是两秒，并且都会修改视图testViewA的属性，但动画执行完毕有不同的操作。单独调用executeAnimationA或者executeAnimationB方法，执行都没有任何问题。

	- (void)viewDidLoad {
    	[super viewDidLoad];
    	
    	//初始化testViewA
    	UIView *testViewA = [[UIView alloc] initWithFrame:CGRectMake(100, 100, 100, 100)];
    	testViewA.backgroundColor = [UIColor redColor];
    	self.testViewA = testViewA;
    }

	-(void)executeAnimationA{
	    [self.view addSubview:self.testViewA];
	    [UIView animateWithDuration:2 animations:^{
	        self.testViewA.frame = CGRectMake(200, 200, 200, 200);
	    } completion:^(BOOL finished) {
	        NSLog(@"animationA finished: %@",finished?@"YES":@"NO");
	        [self.testViewA removeFromSuperview];
	    }];
	}
	
	-(void)executeAnimationB{
	    [self.view addSubview:self.testViewA];
	    [UIView animateWithDuration:2 animations:^{
	        self.testViewA.frame = CGRectMake(0, 0, 300, 300);
	    } completion:^(BOOL finished) {
	        NSLog(@"animationB finished: %@",finished?@"YES":@"NO");
	        self.testViewA.backgroundColor = [UIColor blueColor];
	    }];
	}
	
但是调用test方法，先执行动画A，等待一秒执行动画B，就会发现执行结果完全不正常，动画B执行完之后testView不见了。通过下面的输出发现动画A和动画B都没有正常执行完成，系统都是强行中断了它们的运行:
	
	-(void)test{   
	  	//先执行动画A，等待一秒执行动画B
	    [self executeAnimationA];
	    [self performSelector:@selector(executeAnimationB) withObject:nil afterDelay:1];
	}

	2014-11-27 14:57:54.493 BRYSerialAnimationExample[38825:607] animationA finished: NO
	2014-11-27 14:57:54.496 BRYSerialAnimationExample[38825:607] animationB finished: NO
因为动画A执行过程中，动画B开始执行，它们都会修改相同的视图元素testViewA，所以系统会强行终止动画A而开始动画B的执行。但是动画A的completion中会移除testViewA，执行中的动画B也被强行终止了。

所以可以判断completion返回的finished是否为YES，来判断动画是否正常执行完毕。将代码修改如下。

	- (void)viewDidLoad {
    	[super viewDidLoad];
    	
    	//初始化testViewA
    	UIView *testViewA = [[UIView alloc] initWithFrame:CGRectMake(100, 100, 100, 100)];
    	testViewA.backgroundColor = [UIColor redColor];
    	self.testViewA = testViewA;
    }

	-(void)executeAnimationA{
	    [self.view addSubview:self.testViewA];
	    [UIView animateWithDuration:2 animations:^{
	        self.testViewA.frame = CGRectMake(200, 200, 200, 200);
	    } completion:^(BOOL finished) {
	        NSLog(@"animationA finished: %@",finished?@"YES":@"NO");
	        if(finished){
	            [self.testViewA removeFromSuperview];
	        }
	    }];
	}
	
	-(void)executeAnimationB{
	    [self.view addSubview:self.testViewA];
	    [UIView animateWithDuration:2 animations:^{
	        self.testViewA.frame = CGRectMake(0, 0, 300, 300);
	    } completion:^(BOOL finished) {
	        NSLog(@"animationB finished: %@",finished?@"YES":@"NO");
	        if (finished) {
	            self.testViewA.backgroundColor = [UIColor blueColor];
	        }
	    }];
	}
然后我们再调用test，发现最终效果和我们预期的一致，testViewA最终保持了动画B的效果。但是这样还是比较奇怪，动画A终止动画B开始执行时，testViewA的显示有明显的跳跃。其实这两个动画根本就不应该同时运行，但是难免开发中发生发生这样的情况,我们需要更为详细的解决方法。

####二. 两个用户事件触发的动画冲突简单解决方法:
比如，页面有两个按钮，用户点击按钮A，执行动画A。用户点击按钮B，执行动画B。这两个动画执行过程中都会涉及到同一个视图元素的修改。    
那么，点击按钮A，开始执行动画B，我们可以将按钮B设置为disable，即不响应事件状态。这样动画A在运行过程中用户无法触发按钮B,动画B就不可能执行。

####三. 多个动画引发的动画冲突解决办法:
如果动画不是用户事件触发而是代码调用执行或者有两个以上用户事件会触发动画在同一时刻运行，那么前面的简单方案就不适用了，具体有几种处理方案:

![image]({{ site.baseurl }}/postResource/home.png)   


* **`新动画优先`**: 系统默认的解决方案就是是如果动画A正在执行，动画B开始执行，它们都会修改相同的视图元素。那么系统运行动画B时会直接终止动画A的运行，completion返回参数finished为NO，并且立即开始动画B的执行。
* **`当前动画优先`**: 不执行动画B，不处理按钮B的点击事件。
* **`动画优先级相同，需排队先到先执行`**: 是我们采用动画队列让动画A、动画B都在主线程串行执行，防止动画发生冲突。

####四. 使用串行动画队列解决多个动画间的冲突:
BRYSerialAnimationQueue可以将执行时会修改同一视图元素的动画都加入到动画队列中并依次执行，且动画队列的产生和执行过程不会阻滞主线程（main thread）的执行。
[https://github.com/irace/BRYSerialAnimationQueue](https://github.com/irace/BRYSerialAnimationQueue)
	
	- (void)showMessage {
	    UILabel *label = [[UILabel alloc] init];
	    label.textColor = [UIColor redColor];
	    label.text = @"You'll only see one of me at a time!";
	    label.backgroundColor = [UIColor redColor];
	    [label sizeToFit];
	    [self.view addSubview:label];
	    
	    void (^updateLabelOriginY)(CGFloat) = ^(CGFloat originY) {
	        CGRect frame = label.frame;
	        frame.origin.y = originY;
	        label.frame = frame;
	    };
	    
	    updateLabelOriginY(-CGRectGetHeight(label.frame));
	    
	    [self.queue animateWithDuration:0.5 animations:^{
	        updateLabelOriginY(0);
	    }];
	    
	    [self.queue animateWithDuration:0.5 delay:0.5 options:0 animations:^{
	        updateLabelOriginY(-CGRectGetHeight(label.frame));
	    } completion:^(BOOL finished) {
	        [label removeFromSuperview];
	    }];
	}

####五. 总结
实际开发过程中我们可以根据需要灵活选择解决方案。
