---
layout: post
category : opensource
title:	"curl and libcurl"
tagline: ""
tags : [curl, libcurl, opensource]
---
{% include JB/setup %}

	/*
	 @author: zswood
	 @create: 2016.12.14
	 @brief: 对curl工具及libcurl开源库作简单介绍与分析.
	*/
  

#### *Abstract*
现维护的服务组件需要通过调用外部第三方服务的http接口来实现某功能,由于服务组件用c++进行开发维护并且希望在开发过程中调用过程尽量的简单,能尽快的实现功能并调试通过. 故考虑在该功能的开发过程中直接集成调用开源库libcurl与外部三方服务的http接口之间进行通信,快速简单的实现该功能. 以下为使用libcurl库的相关简略记录信息,作简单的流程性记录(ps:阅览官方文档及示例代码)。


### libcurl
* #### 构建

	github下载源码包解压:
		
		1. ./buildconf
		2. ./configure
		3. ./make
		4. lib/.libs/libcurl.so

	编译支持SSL:

		1. ./buildconf
		2. ./configure --with-ssl	// 需openssl库支持
		3. ./make
		4. lib/.libs/libcurl.so

	*note：configure执行结束会提示支持功能如下*  
	<img src="/picture/opensource/libcurl-and-curl/curl-configure.jpg" alt="curl configure" width="60%" height="60%" />
  
* #### 接口
	常用接口及功能：
* #### 集成
	三方库相关依赖：openssl, crypto, zlib;  
	<img src="/picture/opensource/libcurl-and-curl/libcurl-deps.jpg" alt="curl configure" width="60%" height="60%" />  

	集成调用:
	
* #### 源码

### curl

 
<br/>
> *related links*:  
[https://curl.haxx.se/libcurl/](https://curl.haxx.se/libcurl/)  
[https://github.com/curl/curl](https://github.com/curl/curl)
