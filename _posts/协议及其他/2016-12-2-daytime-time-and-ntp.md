---
layout: post
category : protocol and other
title:	"网络时间协议ntp相关"
tagline: ""
tags : [daytime, time protocol, ntp, network time protocol, 时间协议]
---
{% include JB/setup %}

	/*
	 @author: zswood
	 @create: 2016.12.2
	 @brief: 记录网络时间协议ntp相关的部分内容,便于对ntp有一个直观的了解.
	*/
  
  

#### 前情
最近某同学在工作中用到了阿里云的服务。在向阿里云服务发起请求时,阿里云会对请求的时间进行校验(校验时间范围大概10min以内)，如果应用的本地时间和服务端相差过大阿里云则认为请求超时会拒绝服务并返回相应错误码。同学便向我问到了时间同步的问题，鉴于此我也去了解了一下时间同步相关的问题，整理如下:

<br/>
### RFC867 Daytime Protocol  
daytime服务的作用很简单,daytime服务接收到一个client连接随即给该用户返回一个字符串数据(你只要给对应的ip:port发起connect连接,甚至不需要send数据就可以直接调用recv获取服务端返回的字符串,字符串的内容即为daytime服务器的当前日期及时间;

daytime服务使用13端口,tcp及udp均支持;

daytime服务足够简单便捷,但RFC867标准并未规定daytime协议的数据格式,所以不同的daytime服务返回的时间格式也是不同的.用户请求不同的服务需要自己实现相应的解析;如美国标准技术院daytime服务(time.nist.gov);

		code
		time format example

### RFC868 Time Protocol  

### RFC1305 Network Time Protocol(v3)
