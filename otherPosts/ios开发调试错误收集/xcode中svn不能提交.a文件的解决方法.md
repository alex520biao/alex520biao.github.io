
###Xcode中SVN不能提交.a文件的解决方法
----
XCode不能提交.a文件,并且显示i提示。i即为svn中的ignores。
这个与SVN的配置有关, 其实与xcode倒没有关系. 解决方法:

1. 打开终端,  在命令行中输入如下命令来打开配置文件。
		
		open ~/.subversion/config
		
2. 然后, 在[miscellany]项找到这个串:  
		
		# global-ignores = *.o *.lo *.la *.al .libs *.so *.so.[0-9]* *.a *.pyc *.pyo
		#   *.rej *~ #*# .#* .*.swp .DS_Store

	这里的意思是, SVN在提交时自动忽略以这些后缀的文件, 那么我们要去掉*.a这一项, 则将配置文件改为:
			
		global-ignores = *.o *.lo *.la *.al .libs *.so *.so.[0-9]*  *.pyc *.pyo *.rej *~ #*# .#* .*.swp .DS_Store   
3. 保存退出. 就可以了。
	>你可以根据自己的需要修改其他的后缀名。


###采用命令行直接提交
在这次开发中，多次碰到这个问题。.a文件在xcode里，没有版本的显示，新添加上来的，也没有用。
我就郁闷了。后来发现，所有的.a文件在Xcode上都没有版本信息。

解决方法如下:     

1. 打开终端，输入以下命令直接添加.a文件:
		
		svn add ../path.../path.../xxx.a
2. 然后在Xcode上就可以看到scm上，标识为A了，再提交版本就可以了。
 
###引用参考
1. [http://wpt205.blog.163.com/blog/static/108047495201371272034579/](http://wpt205.blog.163.com/blog/static/108047495201371272034579/)
2. [http://www.cocoachina.com/bbs/read.php?tid-2226.html](http://www.cocoachina.com/bbs/read.php?tid-2226.html)   
3. [http://blog.itpub.net/10531/viewspace-710948](http://blog.itpub.net/10531/viewspace-710948)


