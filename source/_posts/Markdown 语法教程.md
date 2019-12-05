---
title: Markdown 语法
top: true
cover: false
toc: true
mathjax: false
date: 2019-10-20 21:50:28
author: qin nian
img:
coverImg:
password: 
summary: 算是最全的了吧（不全评论戳我）
tags: 
- Markdown
categories: 网站建设
---

## 写在前面

Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式。

优点：

- 让作者摆脱排版的困扰，专心写作。

- 操作简单。

缺点：

- 需要记一些语法（当然，是很简单。五分钟学会）。

- 有些平台不支持Markdown编辑模式。

> 申明：我使用的是Visual Studio Code 编辑器

## 一、标题

示例：

    # 这是一级标题

    ## 这是二级标题

    ### 这是三级标题

    #### 这是四级标题

    ##### 这是五级标题

    ###### 这是六级标题

效果如下：

![标题](https://i.loli.net/2019/10/26/h2pyGtWQmRg7Jxd.png)

## 二、字体

示例：

    *斜体1*  、  _斜体2_  、  <i>斜体3</i>  、  <em>斜体4</em>  

    **加粗**  、  <b>加粗2</b> 

    ***加粗斜体1***  、 **_加粗斜体2_**  

    ~~删除1~~  、  <del>删除2</del>  

    <u>下划线</u>   

    Z<sup>a</sup>  

    Z<sub>a</sub>  

效果如下：

![字体](https://i.loli.net/2019/10/26/QMosHkXW5ytaIgZ.png)

## 三、引用

示例：

    >这是引用的内容
    >>这是引用的内容
    >>>>>>>>>>这是引用的内容

![引用](https://i.loli.net/2019/10/31/5Mihu1wzQJYem2E.png)

## 四、分割线

示例：
    ---

    ***

    -----

    *****

    -------

    *******

效果如下：

![分割线](https://i.loli.net/2019/10/31/Tc3sLUkQn5OpSvh.png)

## 五、图片

### 1、普通展示图片

示例：

    ![猫咪](猫咪地址链接)
    或
    <img src="猫咪地址链接" >

效果如下：

![猫咪](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=2244238741,1217077712&fm=5)

### 2、img 标签控制宽高

示例：

    <img src="猫咪地址链接"  height="100" width="100">

效果如下：

<img src="https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=2244238741,1217077712&fm=5"  height="100" width="100">

### 3、div 标签和 align 属性控制对齐方式

示例：

    <div align="center">

    <img src="猫咪地址链接"  height="100" width="100">

    </div>

效果如下：

<div align="center">
<img src="https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=2244238741,1217077712&fm=5"  height="100" width="100">
 </div>

## 六、超链接

示例：

    [钦念博客1](http://www.qinnian.xyz)

    <a href="http://www.qinnian.xyz" target="_blank">钦念博客2</a>

效果如下：

[钦念博客2](http://www.qinnian.xyz)

<a href="http://www.qinnian.xyz" target="_blank">钦念博客2</a>

## 七、列表

### 1、无序列表

示例：

    - 无序列表1

    + 无序列表2

    * 无序列表3

效果如下：

![无序列表](https://i.loli.net/2019/10/26/4CPzgk7YHF3pfqN.png)

### 2、有序列表

示例：

    1. 有序列表

    2. 有序列表

    3. 有序列表

效果如下：

![有序列表](https://i.loli.net/2019/10/26/CsYNOkvjXJxtA5m.png)

### 3、列表嵌套

示例：

> 上一级和下一级之间敲三个空格即可

    - 无序列表

       - 无序列表1

       - 无序列表2

       - 无序列表3

    1. 有序列表

        1. 有序列表

        2. 有序列表

        3. 有序列表

效果如下：

![列表嵌套](https://i.loli.net/2019/10/26/WGPM32BAckIESFK.png)

## 八、表格

示例：

    表头|表头|表头
    ---|:--:|---:
    内容|内容|内容
    内容|内容|内容

效果如下：

![表格](https://i.loli.net/2019/10/26/GE6n1fSZDX9rTgW.png)

## 九、代码

### 1、单行代码

示例：

    `代码内容`

效果如下：

 `代码内容`

### 2、代码块

示例：

> 选中，按Tab键

![代码块](https://i.loli.net/2019/10/26/b6Nl4VPFejzvAST.png)

效果如下：

    代码...
    代码...
    代码...
