---
layout: post
category : zswood prj
title:	"windows语音识别demo"
tagline: ""
tags : [iflytek, asr, windows]
---
{% include JB/setup %}

	/*
	 @author: zswood
	 @create: 2017.01.11
	 @brief: .
	*/
  

#### *Abstract*

0. ilfytek speech api(include iat, its and tts)

1. windows lib load api
	i. 涉及的windows api;
	ii. dll load api;
	iii. audio record;

2. windows record api
	i. 录音接口
	ii.播放/回放接口
	
3. Character encoding
字符编码起源,定义,检测及转换
utf8, gb2312, unicode, 
/*windows*/
MultiByteToWideChar()
WideCharToMultiByte()

/*linux*/
iconv_open()
iconv()
iconv_close()

3. 数据格式校验及解析(json,xml)

4. 配置类+日志类;

5. windows 图形界面编程