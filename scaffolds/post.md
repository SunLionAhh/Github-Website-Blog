---
title: {{ title }}             #  文章标题，强烈建议填写此选项
date: {{ date }}               #  发布时间，强烈建议填写此选项，且最好保证全局唯一
author: Qin Nian               #  文章作者
img: /source/images/xxx.jpg    #  文章特征图，推荐使用图床(腾讯云、七牛云、又拍云等)来做图片的路径.
coverImg:                      #  表示该文章在首页轮播封面需要显示的图片路径，如果没有，则默认使用文章的特色图片
top: true                      #  推荐文章（文章是否置顶），如果 top 值为 true，则会作为首页推荐文章
toc: true                      #  是否开启 TOC，需在主题的 _config.yml 中激活了 toc 选项
cover: false                   #  表示该文章是否需要加入到首页轮播封面中
mathjax: false                 #  是否开启数学公式支持,需在主题的 _config.yml 中激活
password: 文章阅读密码          #  SHA256 加密。需在主题的 config.yml 中激活 verifyPassword
summary:                       #  文章摘要，自定义的文章摘要内容
categories:                    #  文章分类，建议一篇文章一个分类
tags:                          #  文章标签，一篇文章可以多个标签
    - Markdown
    - Typora
---