---
layout: post
title: You're up and running!
---

Next you can update your site name, avatar and other options using the _config.yml file in the root of your repository (shown below).

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.

####测试链接:外部调用进入顺风车相关页面或服务
1. 外部调起进入披头士首页URL 
[diditravel://com.didi.passengerapp/beatles_homepage?productid=259&userrole=1](diditravel://com.didi.passengerapp/beatles_homepage?productid=259&userrole=1)
2. 外部调起进入披头士司机订单详情页(如果订单已被抢则需要routeid) 
[diditravel://com.didi.passengerapp/beatles_driver_orderdetail?productid=259&orderid=1234&routeid=xxxx&one_to_one=0](diditravel://com.didi.passengerapp/beatles_driver_orderdetail?productid=259&orderid=1234&routeid=xxxx&one_to_one=0)
3. 外部调起进入披头士乘客订单详情页URL 
[diditravel://com.didi.passengerapp/beatles_passenger_orderdetail?productid=259&orderid=12341&one_to_one=0](diditravel://com.didi.passengerapp/beatles_passenger_orderdetail?productid=259&orderid=12341&one_to_one=0)
4. 外部调起进入披头士通用运营web页面
[diditravel://com.didi.passengerapp/beatles_webpage?productid=259&weburl=http%3a%2f%2fwww.hao123.com%2f](diditravel://com.didi.passengerapp/beatles_webpage?productid=259&weburl=http%3a%2f%2fwww.hao123.com%2f)   

5. 顺风车乘客发单页(订单)
[diditravel://com.didi.passengerapp/beatles/passenger_createorder?productid=259&is_carpool=1](diditravel://com.didi.passengerapp/beatles/passenger_createorder?productid=259&is_carpool=1)

	参数说明: is_carpool参数说明文档

6. 顺风车司机发单页(线路)
[diditravel://com.didi.passengerapp/beatles/driver_publishroute?productid=259](diditravel://com.didi.passengerapp/beatles/driver_publishroute?productid=259)

7. 顺风车车主附近订单列表页
[diditravel://com.didi.passengerapp/beatles/driver_nearorderlist?productid=259&filter=0](diditravel://com.didi.passengerapp/beatles/driver_nearorderlist?productid=259&filter=0)

	参数说明: filter参数说明文档

8. 顺风车车主跨城订单列表页
[diditravel://com.didi.passengerapp/beatles/driver_crosscitylist?productid=259&filter=0](diditravel://com.didi.passengerapp/beatles/driver_crosscitylist?productid=259&filter=0)

	参数说明: filter参数说明文档

9. 顺风车车主顺路订单列表页
[diditravel://com.didi.passengerapp/beatles/driver_onewaylist?productid=259&filter=0](diditravel://com.didi.passengerapp/beatles/driver_onewaylist?productid=259&filter=0)

	参数说明: route_id和filter参数说明文档

####通用测试页
[diditravel://com.didi.passengerapp/beatles_webpage?productid=259&weburl=https%3a%2f%2falex520biao.github.io%2fHello-World%2f](diditravel://com.didi.passengerapp/beatles_webpage?productid=259&weburl=https%3a%2f%2falex520biao.github.io%2fHello-World%2f)