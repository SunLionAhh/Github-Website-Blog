---
title: Visual Studio 2010 配置 OpenGL
top: false
cover: false
toc: true
mathjax: false
date: 2019-11-01 21:50:28
author: qin nian
img:
coverImg:
password: 
summary: VS2010，跟我右边画一道彩虹
tags: 
- OpenGL
categories: Computer Graphics
---

## 1. 写在前面

确保自己安装了 `VS2010` (安装路径自己不要忘记)

## 2. 下载GLUT

>`GLUT`（英文全写：`OpenGL Utility Toolkit`）是一个处理OpenGL程式的工具库，负责处理和底层操作系统的呼叫以及I/O。

Windows环境下的GLUT下载地址： [点这里](http://www.opengl.org/resources/libraries/glut/glutdlls37beta.zip)

解压后会得到5个文件：

>`glut.h`、`glut.lib`、`glut32.lib`、`glut.dll`、`glut32.dll`

## 3. VS2010 环境配置

### 3.1 移动文件（以我的安装路径为例）

1. `glut.h` 复制到 `D:\VS 2010\VC\include\GL`

2. `glut.lib`、`glut32.lib`复制到 `D:\VS 2010\VC\lib`

3. `glut.dll`、`glut32.dll`复制到`C:\Windows\System32`(32位)或`C:\Windows\SysWOW64`(64位)

### 3.2 附加依赖项

1. 打开 `VS 2010` ,随便打开或者新建一个项目

2. 打开`附加依赖项`这个框
    >`project`->`project property`-> `Configuration Properties`->`Linker`->`Input`->`Additional Dependencies`（英文版）
    >
    > 项目->属性-> 配置属性->链接器->输入->附加依赖项 （中文版）

3. 添加

     `opengl32.lib`

     `glu32.lib`

     `glut32.lib`
