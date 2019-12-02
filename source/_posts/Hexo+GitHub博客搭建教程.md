---
title: 博客搭建教程
top: true
cover: false
toc: true
mathjax: false
date: 2019-10-20 21:50:28
author: qin nian
img:
coverImg:
password: 
summary: 我一步一步写出教程来了
tags: 
- Hexo
- Github
categories: 网站建设
---
## 写在前面

2019年9月开始搭建博客，这两个月的时间学习各种知识。这次用 `Hexo+Github` 把博客搭建完成。现在将自己搭建过程中所学详细记录。

---

## 第一部分 搭建

### 1.安装Git

Git是目前世界上最先进的分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。也就是用来管理你的hexo博客文章，上传到GitHub的工具。[【廖雪峰Git教程】](https://www.liaoxuefeng.com/wiki/896043488029600/896202815778784)

git官网下载，[Download git](https://gitforwindows.org/)，下载后会有一个 `Git Bash` 的命令行工具，以后就用这个工具来使用git。

安装好后，用 `git --version` 来查看一下版本

![检查git版本](https://i.loli.net/2019/10/29/36Z1JDyKTx7wbXm.png)

### 2.安装Node.js

`Hexo`基于`Node.js`，需要安装一下`Node.js`和里面的`npm`工具。

Nodejs选择LTS版本,安装选项全部默认，一路点击`Next`。[【Node.js下载地址】](http://nodejs.cn/download/)

安装后，按 `Win+R` 打开命令提示符 输入`cmd`

    node -v
    npm -v

检查一下有没有安装成功(出现序列号就安装完成了)

![检查Node.js和npm工具](https://i.loli.net/2019/10/29/TPMfvpUWNSC3Xie.png)

>windows在git安装完后，就可以直接使用git bash来敲命令行了，不用自带的cmd

### 3.安装Hexo

Hexo是一款基于Node.js的静态博客框架，依赖少易于安装使用，可以方便的生成静态网页托管在GitHub和Coding上，是搭建博客的首选框架。大家可以进入hexo官网进行详细查看，因为Hexo的创建者是台湾人，对中文的支持很友好，可以选择中文进行查看。

官网： [http://hexo.io](http://hexo.io)

github: [https://github.com/hexojs/hexo](https://github.com/hexojs/hexo)

前面git和nodejs安装好后，就可以安装hexo了

1. 创建一个文件夹Blog，用来存放自己的博客文件，在这个文件夹下直接右键git bash打开。

2. 输入 `npm install -g hexo-cli` 安装Hexo。安装完后输入 `hexo -v` 验证是否安装成功。

    ![检查是否安装Hexo](https://i.loli.net/2019/10/29/qGpWsJvMwIA9bro.png)

3. 初始化一下hexo,即初始化我们的网站，输入`hexo init`初始化文件夹。然后，接着输入`npm install`安装必备的组件。

4. 输入`hexo g`生成静态网页，然后输入`hexo s`打开本地服务器。

5. 浏览器打开[【http://localhost:4000/】](http://localhost:4000/) 就可以看到我们的博客了，按ctrl+c关闭本地服务器。

    ![页面效果](https://i.loli.net/2019/10/29/NkiHKo4AVWhdCR9.png)

新建完成后，指定文件夹MyBlog目录下有：

- node_modules: 依赖包
- public：存放生成的页面
- scaffolds：模版文件。当你创建一篇新的文章时，hexo会依据模版文件进行创建，主要用在你想在每篇文章都添加一些共性的内容的情况下
- source：用来存放你的文章。除了文章还有一些主要的资源，比如文章里的图片，文件等等东西。这个文件夹最好定期做一个备份，丢了它，整个站点就废了。
- themes：主题文件夹
- _config.yml 站点配置文件。很多全局配置都在这个文件中
- package.json 应用数据。可以看出hexo版本信息，以及它所默认或者说依赖的一些组件

### 4.GitHub创建个人仓库

1. 注册一个github账号[【Github官网】](https://github.com/)

2. 我的主页 [https://github.com/qinnian](https://github.com/qinnian) ，那么我的用户名为“qinnian”

3. 新建一个名为 `用户名.github.io` 的仓库

4. 将来网站访问地址就是 [http://qinnian.github.io](http://qinnian.github.io)

    ![创建仓库](https://i.loli.net/2019/10/29/3ivgEz2pBFdsbIL.png)

### 5.配置SSH key

使用ssh key来解决本地和服务器的连接问题。ssh，简单来讲，就是一个秘钥，其中，id_rsa是你这台电脑的私人秘钥，不能给别人看的，id_rsa.pub是公共秘钥，可以随便给别人看。把这个公钥放在GitHub上，这样当你链接GitHub自己的账户时，它就会根据公钥匹配你的私钥，当能够相互匹配时，才能够顺利的通过git上传你的文件到GitHub上

1. 输入 `~/. ssh` 检查本机是否存在的ssh密钥。

2. 设置user.name和user.email配置信息

        git config --global user.name "你的GitHub用户名"

        git config --global user.email "你的GitHub注册邮箱"

3. 生成ssh密钥文件：

       ssh-keygen -t rsa -C "你的GitHub注册邮箱"

4. 然后连续3次回车，最终会生成一个文件在用户目录下，打开C盘用户目录，找到 `.ssh\id_rsa.pub` 文件，记事本打开并复制里面的内容。

5. 打开你的github主页，进入个人设置 -> SSH and GPG keys -> [New SSH key](https://github.com/settings/keys)：将刚复制的内容粘贴到key那里，`title`随便填，保存。

6. 在 git bash 输入 `ssh -T git@github.com` 检验是否搭建完成。

    ![配置SSH key 成功](https://i.loli.net/2019/10/29/nGKMZPw47otFajk.png)

### 6.将hexo部署到GitHub

我们就可以将`hexo`和`GitHub`关联起来，也就是将`hexo`生成的文章部署到`GitHub`上，打开`Blog`根目录下的`_config.yml`文件，这是博客的配置文件，在这里你可以修改与博客配置相关的各种信息。

修改最后一行的配置：

    deploy:

      type: git

      repo: https://github.com/qinnian/qinnian.github.io.git

      branch: master

`repository`修改为你自己的`github`项目地址即可，就是部署时，告诉工具，将生成网页通过`git`方式上传到你对应的链接仓库中。

这个时候需要先安装`deploy-git` ，也就是部署的命令,这样你才能用命令部署到`GitHub`。

    npm install hexo-deployer-git --save

然后

    hexo clean    //清除了你之前生成的东西

    hexo generate  //生成静态文章，可以用 hexo g 缩写 

    hexo deploy   //部署文章，可以用 hexo d 缩写 

![网页](https://i.loli.net/2019/10/29/NGtspZ5uYSADb6w.png)

### 7.设置个人域名

现在你的个人网站的地址是 `qinnian.github.io`，如果觉得这个网址逼格不太够，这就需要你设置个人域名了。但是需要花钱。

1. 首先你得购买一个专属域名(我在腾讯买的，微信支付)

    ![image.png](https://i.loli.net/2019/10/29/pe4lxrYKSbaQf9M.png)

2. 打开你本地博客`/source`目录，新建`CNAME`文件，注意没有后缀。然后在里面写上你的域名，保存。最后运行 `hexo g` 、 `hexo d` 上传到github。

    ![CNAME](https://i.loli.net/2019/10/29/jskNyKVPM31oECx.png)

3. 这时候你的`Github`项目根目录应该会出现一个名为`CNAME`的文件了。然后打开你的`github`博客项目，点击`settings`，拉到下面`Custom domain`处，你也会发现自己的域名 (例如我的是qinnian.xyz）。

    ![settings](https://i.loli.net/2019/10/29/cvVO4bpwNSKEG7l.png)

4. 过不了多久，再打开你的浏览器，输入你自己的专属域名，就可以看到搭建的网站啦！

    ![域名设置成功](https://i.loli.net/2019/10/29/IdG7SVYf6msPnOh.png)

### 8.发布文章

1. 在`Blog`根目录下右键打开 `git bash` ，安装一个扩展 `npm i hexo-deployer-git`

2. 新建一篇文章输入 `hexo new post "title"`。比如要新建一个叫《博客搭建教程》的文章,则 `hexo new post "博客搭建教程"`打开 `Blog\source\_posts` 的目录，下面多了一个文件夹和一个 `.md` 文件，就是你的文章文件。

    ![文章文件](https://i.loli.net/2019/10/29/WGKBPg75uZdh4rJ.png)

3. 根目录下

        hexo g //生成静态网页

        hexo s //本地预览效果

        hexo d //上传到 github

 这时打开你的 `Blog` 主页就能看到发布的文章

---

## 第二部分 配置

### 1.Blog目录_config.yml修改

在文件根目录下的 _config.yml ，就是整个 hexo 框架的配置文件了。可以在里面修改大部分的配置。详细可参考官方的[配置描述](https://hexo.io/zh-cn/docs/configuration)。

#### （1）网站 Site

![Site](https://i.loli.net/2019/10/29/QCn6vN4hlWB7rTt.png)

#### （2）网址 URL

![URL](https://i.loli.net/2019/10/29/1OCia7Brfk8DmIJ.png)

>在这里，你需要把 `url` 改成自己的网站域名。

#### （3）目录 Directory

![Directory](https://i.loli.net/2019/10/29/KkWyrfbdUPYO962.png)

>刚刚开始接触 Hexo，通常没有必要修改这一部分的值。

#### （4）文章 Writing

![Writing](https://i.loli.net/2019/10/29/9ktpur2dTbKQPzF.png)

> 刚刚开始接触 Hexo，通常没有必要修改这一部分的值。

#### （5）分页 per_page

![per_page](https://i.loli.net/2019/10/29/w856Gu3lTaOmoIh.png)

> 建议修改两个 per_page 的分页条数值为 6 的倍数，如：12、18 等，这样文章列表在各个屏幕下都能较好的显示。

#### （6）主题 Themes

在 `themes` 这个文件夹下默认给你安装的是 `lanscape` 这个主题。当你需要更换主题时，在官网上下载，把主题的文件放在 `themes` 文件夹下，再修改这个主题参数就可以了。

点击 [这里](https://codeload.github.com/blinkfox/hexo-theme-matery/zip/master) 下载 `master` 分支的最新稳定版的代码，解压缩后，将 `matery` 的文件夹复制到你 `Blog` 的 `themes` 文件夹中即可。

当然你也可以在你的 `themes` 文件夹下使用 `Git clone` 命令来下载:

    git clone https://github.com/blinkfox/hexo-theme-matery.git

![matery](https://i.loli.net/2019/10/29/iZ4sFR93GvwIzgf.png)

> 修改 `theme` 的值：`theme: matery`
>
> 文件名和主题参数名称一致就行，这边我重命名为`matery`

最后打开网页

![网页效果](https://i.loli.net/2019/10/29/inKgOVkQHfeYzUh.png)

### 2.新建文章模板修改

为了新建文章方便，我们可以修改一下文章模板，建议将 `/scaffolds/post.md` 修改为如下代码：

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

这样新建文章后 一些 `Front-matter` 参数不用你自己补充了，修改对应信息就可以了

注意:

> 1. 如果 `img` 属性不填写的话，文章特色图会根据文章标题的 `hashcode` 的值取余，然后选取主题中对应的特色图片，从而达到让所有文章都的特色图各有特色。
> 2. `date` 的值尽量保证每篇文章是唯一的，因为本主题中 `Gitalk` 和 `Gitment` 识别 `id` 是通过 `date` 的值来作为唯一标识的。
> 3. 如果要对文章设置阅读验证密码的功能，不仅要在 Front-matter 中设置采用了 SHA256 加密的 password 的值，还需要在主题的 `_config.yml` 中激活了配置。有些在线的 SHA256 加密的地址，可供你使用：[开源中国在线工具](http://tool.oschina.net/encrypt?type=2)、[chahuo](http://encode.chahuo.com/)、[站长工具](http://tool.chinaz.com/tools/hash.aspx)。

### 3.新建分类页面

#### （1）categories 页

> 用来展示所有分类的页面

    hexo new page "categories"

编辑你刚刚新建的页面文件 /source/categories/index.md

    ---
    title: categories
    date: 2019-10-12 00:00:00
    type: "categories"
    layout: "categories"
    ---

#### （2）tags 页

> 用来展示所有标签的页面

    hexo new page "tags"

编辑你刚刚新建的页面文件 /source/tags/index.md

    ---
    title: tags
    date: 2019-10-12 00:00:00
    type: "tags"
    layout: "tags"
    ---

#### （3）about 页

> 用来展示关于我和我的博客信息的页面

    hexo new page "about"

编辑你刚刚新建的页面文件 /source/about/index.md

    ---
    title: about
    date: 2019-10-12 00:00:00
    type: "about"
    layout: "about"
    ---

#### （4）contact 页

> 用来展示留言板信息的页面

留言板功能依赖于第三方评论系统，激活你的评论系统才有效果。

并且在主题的 _config.yml 文件中，第 19 至 21 行的“菜单”配置，取消关于留言板的注释

    hexo new page "contact"

编辑你刚刚新建的页面文件 /source/contact/index.md

    ---
    title: contact
    date: 2019-10-12 00:00:00
    type: "contact"
    layout: "contact"
    ---

#### （5）friends 页

> 用来展示友情连接信息的页面

    hexo new page "friends"

编辑你刚刚新建的页面文件 /source/friends/index.md：

    ---
    title: friends
    date: 2019-10-12 00:00:00
    type: "friends"
    layout: "friends"
    ---

同时，在你的博客 source 目录下新建 _data 目录，在 _data 目录中新建 friends.json 文件，文件内容如下所示：

    [
        {
            "avatar": "https://ss1.baidu.com/70cFfyinKgQFm2e88IuM_a/forum/pic/item/7c1ed21b0ef41bd55eec003854da81cb38db3dbb.jpg",
            "name": "STD_BUPT",
            "introduction": "钦念考研",
            "url": "https://www.cnblogs.com/qinnian/",
            "title": "冲鸭"
        }
    ]

#### （6）添加404页面

首先在 `/source/` 目录下新建一个`404.md`，内容如下：

    ---
    title: 404
    date: 2019-08-5 16:41:10
    type: "404"
    layout: "404"
    description: "Oops～，我崩溃了！找不到你想要的页面 :("
    ---

然后在 `/themes/matery/layout/` 目录下新建一个 `404.ejs` 文件，内容如下：

    <style type="text/css">
        /* don't remove. */
        .about-cover {
            height: 75vh;
        }
    </style>

    <div class="bg-cover pd-header about-cover">
        <div class="container">
            <div class="row">
                <div class="col s10 offset-s1 m8 offset-m2 l8 offset-l2">
                    <div class="brand">
                        <div class="title center-align">
                            404
                        </div>
                        <div class="description center-align">
                            <%= page.description %>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // 每天切换 banner 图.  Switch banner image every day.
        $('.bg-cover').css('background-image', 'url(/medias/banner/' + new Date().getDay() + '.jpg)');
    </script>

### 4.Themes目录_config.yml修改

#### （1）菜单

（a）配置基本菜单导航的名称、路径url和图标icon

- 菜单导航名称可以是中文也可以是英文(如：Index或主页)

- 图标icon 可以在 `Font Awesome` 中查找

    ![menu](https://i.loli.net/2019/10/29/Na4ByH96TwWsmCp.png)

（b）二级菜单配置方法

- 在需要添加二级菜单的一级菜单下添加children关键字(如:About菜单下添加children)

- 在children下创建二级菜单的 名称name,路径url和图标icon.

- 注意每个二级菜单模块前要加 -.

- 注意缩进格式

        menu:
        Index:
            url: /
            icon: fas fa-home
        Tags:
            url: /tags
            icon: fas fa-tags
        Categories:
            url: /categories
            icon: fas fa-bookmark
        Archives:
            url: /archives
            icon: fas fa-archive
        About:
            url: /about
            icon: fas fa-user-circle-o
        Friends:
            url: /friends
            icon: fas fa-address-book
        Medias:
            icon: fas fa-list
            children:
            - name: Musics
                url: /musics
                icon: fas fa-music
            - name: Movies
                url: /movies
                icon: fas fa-film
            - name: Books
                url: /books
                icon: fas fa-book
            - name: Galleries
                url: /galleries
                icon: fas fa-image

#### （2）建站时间

>修改时间，格式为:月/日/年 时:分:秒.

![time](https://i.loli.net/2019/10/30/javqefMAw9DZb3c.png)

#### （3）首页封面

![cover](https://i.loli.net/2019/10/30/BkteLAawiR9hrfP.png)

#### （4）首页"梦想"

![dream](https://i.loli.net/2019/10/30/AVmXSgRfi9Ent7y.png)

#### （5）首页"音乐"

![music 1](https://i.loli.net/2019/10/30/wrIueFO7v6mkRiU.png)

- 网易云音乐网页版，任意找到一首歌点进去播放，可以在地址栏拿到音乐ID号
- 音乐外链 `http://music.163.com/song/media/outer/url?id=XXXXXX.mp3`， XXXXXX就是歌曲ID号。
- 最后封面图也可以按F12去找页面元素的链接。

![music 2](https://i.loli.net/2019/10/30/xOcvmIY8UKabQFA.png)

> 在source > _data 下新建 musics.json , 填入音乐模块的代码

    [
        {
            "name": "XXX",
            "artise": "XX",
            "url": "https://music.163.com/song/media/outer/url?id=XXXX.mp",
            "cover": ""
        }, 
        {
            "name": "XXX",
            "artise": "XX",
            "url": "https://music.163.com/song/media/outer/url?id=XXXX.mp",
            "cover": "https://p1.music.126.net/yPddBydvnfWXTG2z2FYB2Q==/109951164354997570.jpg"
        }
    ]

#### （6）文章评论

1. GitHub上去新建一个仓库用于存放评论的内容

    ![creat repository](https://i.loli.net/2019/10/30/5q6rDnYJ2p47THx.png)

2. 在设置中打开isue功能

    ![setting](https://i.loli.net/2019/10/30/ZBcdQtOAe1uXxIq.png)

3. 发现默认是打开的

    ![isue](https://i.loli.net/2019/10/30/ZBcdQtOAe1uXxIq.png)
4. 需要注册一个[Github Application](https://github.com/settings/applications/new)

    ![Github Application](https://i.loli.net/2019/10/30/hiO78KAfY9lMwdV.png)

    >注意两个URL就是你网站的域名。应用名称随便写，描述随便写。

5. 完成之后便到了如下页面,其中 `Client ID` 和 `Client Secret` 是我们需要的东西

    ![Client](https://i.loli.net/2019/10/30/Zox6m1qSGpJbPBv.png)

6. 最后设置 Theme 目录下`_config.yml`文件

    ![Gitalk](https://i.loli.net/2019/10/30/FgUDQ9yOToXKRNr.png)

#### （7）其他设置

> 在此文件下更改其他设置，有注解（不会评论教你）

## 第三部分 优化

>先写道这，正在更新中