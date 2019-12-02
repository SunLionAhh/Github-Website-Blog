---
title: windows下使用Microsoft Speech SDK开发包做语音识别
top: false
cover: false
toc: true
mathjax: false
date: 2019-11-27 17:46:28
author: qin nian
img:
coverImg:
password: QN1999
summary: 语音识别
tags: 
- 语音识别
categories: Human Computer Interaction
---

## 一、下载开发包

官网地址：http://www.microsoft.com/en-us/download/details.aspx?id=10121 

下载三个关键的程序：`SpeechSDK51.exe` 、 `msttss22L.exe`、`SpeechSDK51LangPack.exe`

## 二、安装 `SDK`

解压 `SpeechSDK51.exe` 、`SpeechSDK51LangPack.exe` ，分别安装，记住`SpeechSDK51.exe` 安装目录，博主安装在了默认路径下；安装 `msttss22L.exe`

## 三、配置环境（以VS为例）

在应用 `SDK` 的开发前当然得需要对工程环境进行配置，配置的过程如下:

`属性`–`配置属性`–`C/C++`–`常规`–`附加包含目录`，添加一项`C:\Program Files\Microsoft Speech SDK 5.1\Include`到目录中去。

再选择"库目录"项，添加一项 `C:\Program   Files\Microsoft   Speech   SDK   5.1\Lib\i386` 到目录中去.