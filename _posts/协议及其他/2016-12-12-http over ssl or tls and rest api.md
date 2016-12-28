---
layout: post
category : protocol and other
title:	"http https and rest api"
tagline: ""
tags : [http, https, ssl, tls, rest, http协议版本, websocket]
---
{% include JB/setup %}

	/*
	 @author: zswood
	 @create: 2016.12.12
	 @brief: 对http协议相关问题(如http, http over ssl/tls, REST API等)作简单归纳,以备后续查阅.
	*/
  
  

#### 前情
由于我厂外语识别能力目前仅支持英文识别,移动方面某项目期望能够提供更多的语种识别能力,故boss们决定前期先通过调用第三方语音识别接口进行服务封装,同我厂已支持的其他服务统一对外提供识别能力,同时通过该方案采集实际场景外语种识别的有效音频数据集.在对google及nuance两厂识别服务进行简单调研后决定采用nuance识别服务,其中nuance语音识别接口通过http(ios/android sdk)方式对外提供,由于之前并未进行过http形式的接口集成封装工作,对此类调用方式不甚了解,故将涉及相关问题记录如下.


### HTTP  
http即[超文本传输协议](http://baike.baidu.com/item/http),该协议是一种与web服务器进行通信的应用层协议,它与我们的日常紧密联系在一起,我们日常中使用浏览器访问网站的过程其实就是http协议在网站和浏览器之间为我们传输各种需要的信息的过程(当然它的作用不止于此)。  

通常http协议使用80端口(default port)进行消息交互,它定义了一套客户/服务之间进行请求及应答的通信标准:同之前的ntp类似,服务端在指定端口提供相应服务,客户端按照相应格式构造消息(即http协议)并向服务端指定的端口(80端口)进行网络请求,服务端收到请求进行处理后则会返回对应的响应消息(同样遵循http协议),对该响应进行协议解析则得到客户需要的消息;  
![http example picture](/picture/protocol-and-other/http-and-https/http_protocol.jpg)  
 
|	*通用头域*		|		*请求头域*		|		*响应头域*		|		*实体头域*		|
| -------------------- |:--------------------:|:--------------------:|:--------------------:|
| Cache-Control		| 	Accept				| Age				| Allow
| Connection		| 	Accept-Charset		| Location			| Content-Base
| Date(UTC/RFC822)	| 	Accept-Encoding		| Proxy-Authenticate| Content-Encoding
| Pragma			| 	Accept-Language		| Public			| Content-Language
| Transfer-Encoding	| 	Authorization		| Retry-After		| Content-Length
| Upgrade			| 	From				| Server			| Content-Location
| Via				| 	Host(1.1 must)		| Vary				| Content-MD5
|					|	If-Modified-Since	| Warning			| Content-Range
|					|	If-Match			| WWW-Authenticate	| Content-Type
|					|	If-None-Match		|					| Etag
|					|	If-Range			|					| Expires
|					|	If-Unmodified-Since	| 					| Last-Modified
|					|	Max-Forwards		|					| extension-header
|					|	Proxy-Authorization	|					|
|					|	Range				|					|
|					|	Referer				|					|
|					|	User-Agent			|					|
|-----------------------------------| ---------------------------------------- | ---------------------------------------- |--*各头域key具体意义需自查* |
  
请求方法:  
1. OPTINOS  
2. GET  
3. HEAD  
4. POST  
5. PUT  
6. DELETE  
7. TRACE  
8. CONNECT  


响应码:  
 1** :信息响应类  
 2** :处理成功响应类  
 3** :重定向响应类  
 4** :客户端错误类  
 5** :服务端错误类  


* #### RFC1945 http/1.0
http1.0

* #### RFC2616 http/1.1
使用wireshark捕获的简单http交互如下:  
<img src="/picture/protocol-and-other/http-and-https/http_wireshark.jpg" width="60%" height="60%" />


* #### RFC7540 http/2
http当前发布的最新版本,支持多种新特性;

### REST API  

### HTTP Over SSL / HTTP Over TLS  
使用443端口(default)

### Tool&Lib
* #### curl
* #### libcurl
*参见[opensource:libcurl](link:)*
* #### openssl
*参见[opensource:openssl](link:)*

### WebSocket
 
<br/>
> *related links*:  
[https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)  
[https://developer.mozilla.org/zh-CN/docs/Web/HTTP](https://developer.mozilla.org/zh-CN/docs/Web/HTTP)
