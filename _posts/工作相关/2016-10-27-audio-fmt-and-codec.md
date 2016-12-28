---
layout: post
category : work
title:	"音频文件格式及压缩格式"
tagline: ""
tags : [音频格式, 压缩格式, pcm, speex]
---
{% include JB/setup %}

	/*
	 @author: zswood
	 @create: 2016.10.27
	 @brief: 记录相关音频格式及对应音频头协议,及网络传输过程中采用的各类音频压缩解压方法.
	*/

<br/>
### 音频类型
平时工作中常会接触到音频相关的问题,初次接触也许会对wav,pcm,vox,a律,μ律等词汇感到迷惑不易分辨,在使用cooledit对音频进行处理后保存的过程中也会发现可以选择的音频数据格式种类实在是繁多,要想搞清楚这各类音频格式之间的区别实在是一件烦恼事,故在此对常见的音频格式作简单记录.(*cooledit存储各类音频类型如下图*)

![cooledit存储音频类型](/picture/work/audio-fmt-and-codec/cooledit_aufmt.jpg)  
<br/>  

#### 首先给出如下各基本概念的定义
音频格式VS音频编码(参见google语音编码文档)
PCM:  

WAV:  

A律：  

μ律：  

音频信号:  
音频格式:  
模拟信号:  


以下为部分格式音频数据前段的二进制头信息:  
1. PCM Raw Data  
![PCM Raw Data文件头](/picture/work/audio-fmt-and-codec/pcm_raw_data.jpg)  
2. Windows PCM  
![Windows PCM文件头](/picture/work/audio-fmt-and-codec/windows_pcm.jpg)  
3. ACM Waveform  
![ACM Waveform文件头](/picture/work/audio-fmt-and-codec/ACM_Waveform.jpg)  
4. A/mu-Law Wave  
![A/mu-Law Wave文件头](/picture/work/audio-fmt-and-codec/A-mu_law.jpg)  
5. mp3PRO?(FhG)  
![mp3PRO?(FhG)文件头](/picture/work/audio-fmt-and-codec/mp3PRO.jpg)  
6. 64-bit doubles  
![64-bit doubles文件头](/picture/work/audio-fmt-and-codec/64_bit_double.jpg)
<br/>
<br/>

* #### 文件格式

		// windows pcm文件头信息; 44 Byte;
		struct wave_pcm_hdr
		{
			char		riff[4];			// = "RIFF"
			SR_DWORD		size_8;				// = FileSize - 8
			char		wave[4];			// = "WAVE"
			char		fmt[4];				// = "fmt "
			SR_DWORD		dwFmtSize;			// = 下一个结构体的大小 : 16

			SR_WORD		format_tag; 			// = PCM : 1
			SR_WORD		channels;			// = 通道数 : 1
			SR_DWORD		samples_per_sec;		// = 采样率 : 8000 | 6000 | 11025 | 16000
			SR_DWORD		avg_bytes_per_sec;		// = 每秒字节数 : dwSamplesPerSec * wBitsPerSample / 8
			SR_WORD		block_align;			// = 每采样点字节数 : wBitsPerSample / 8
			SR_WORD		bits_per_sample; 		// = 量化比特数: 8 | 16

			char		data[4];			// = "data";
			SR_DWORD	data_size;	 			// = 纯数据长度 : FileSize - 44 
		};
* 
		// A/μ律音频文件头信息; 58 Byte;
		struct wave_aulaw_hdr
		{
			char		riff[4];			// = "RIFF"
			SR_DWORD		size_8;				// = FileSize - 8
			char		wave[4];			// = "WAVE"
			char		fmt[4];				// = "fmt "
			SR_DWORD		fmt_size;			// = 下一个结构体的大小 : 18
		
			SR_WORD		format_tag; 			// = aLaw : 6 | uLaw : 7
			SR_WORD		channels;			// = 通道数 : 1
			SR_DWORD		samples_per_sec;		// = 采样率 : 8000 | 6000 | 11025 | 16000
			SR_DWORD		avg_bytes_per_sec;		// = 每秒字节数 : dwSamplesPerSec * wBitsPerSample / 8
			SR_WORD		block_align;			// = 每采样点字节数 : wBitsPerSample / 8
			SR_WORD		bits_per_sample; 		// = 量化比特数: 8 | 16
			SR_WORD		cbsize;				// = 下一个结构体的大小 : 0

			char		fact[4];			// = "fact"
			SR_WORD		unknown1;			// = 4;
			SR_WORD		unknown2;			// = 0;
			SR_DWORD		data_size_raw; 			// = Datasize : FileSize - 58

			char		data[4];			// = "data";
			SR_DWORD		data_size;	 		// = DataSize : FileSize - 58
		};

* #### 采样率(Sample Rate)  
  顾名思义,采样率即采样的频率,即采样过程中从连续声学信号中提取采样点组成离散信号的频率(单位:Hz),录音设备每秒内对声音信号的采样次数。不同的需求会采取不同的采样率进行音频录制;采样频率越高,音频的还原度就越高,同样的音频大小也就会越大;  
  
  一般而言:  电话信道采用8k采样(欧洲、中国:[A律](http://baike.baidu.com/view/3871220.htm); 北美、日本:[μ律](http://baike.baidu.com/view/3871221.htm));CD音质为44.1k采样(人耳范围:20Hz~20KHz,由[采样定理](http://baike.baidu.com/view/472214.htm)>*2);语音识别一般采用8/16k采样音频;

  ![wave properties](/picture/work/audio-fmt-and-codec/wave_para.jpg)  


* #### 声道(Channels)  
  

* #### 量化位数(Digitalizing bit),位深度
  16bit，振幅范围(截幅)，分贝;
  分贝至振幅换算;
  

* #### 文件大小  
  PCM  
  A/mu-Law  


### 压缩格式
(eg:speex,amr,ico,aac,etc...);


### 音频重采样
* [libspeexdsp](https://www.speex.org/ "speex.org")
* 