---
layout: post
title: You're up and running!
---

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.

####测试链接:外部调用进入顺风车相关页面或服务
1. 外部调起进入披头士首页URL 
[diditravel://com.didi.passengerapp/beatles_homepage?productid=259](diditravel://com.didi.passengerapp/beatles_homepage?productid=259)
2. 外部调起进入披头士司机订单详情页(如果订单已被抢则需要routeid) 
[diditravel://com.didi.passengerapp/beatles_driver_orderdetail?productid=259&orderid=1234&routeid=xxxx](diditravel://com.didi.passengerapp/beatles_driver_orderdetail?productid=259&orderid=1234&routeid=xxxx)
3. 外部调起进入披头士乘客订单详情页URL 
[beatles_passenger_orderdetail?productid=259&orderid=12341](beatles_passenger_orderdetail?productid=259&orderid=12341)
4. 外部调起进入披头士通用运营web页面
[diditravel://com.didi.passengerapp/beatles_webpage?productid=259&weburl=http%3a%2f%2fwww.hao123.com%2f](diditravel://com.didi.passengerapp/beatles_webpage?productid=259&weburl=http%3a%2f%2fwww.hao123.com%2f)

####通用测试页
[diditravel://com.didi.passengerapp/beatles_webpage?productid=259&weburl=https%3a%2f%2falex520biao.github.io%2fHello-World%2f](diditravel://com.didi.passengerapp/beatles_webpage?productid=259&weburl=https%3a%2f%2falex520biao.github.io%2fHello-World%2f)