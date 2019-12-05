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
summary: 优化过程未完待续
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

> 在此文件下更改其他设置，查看 `Hexo` 官网

## 第三部分 优化

### 1、添加博客天气插件

中国天气网：[https://cj.weather.com.cn/plugin/pc](https://cj.weather.com.cn/plugin/pc)


将下面代码插入 `/themes/matery/layout/_partial/layout.ejs` 中

    <script type="text/javascript">
        WIDGET = {FID: '1tFpFZ5Mtj'}
    </script>
    <script type="text/javascript" src="https://apip.weatherdt.com/float/static/js/r.js?v=1111"></script>

### 2、添加博客动态标签

原理就是给博客增加一个事件判断，如下图所示：

![点击前](https://ae01.alicdn.com/kf/Hd6ddeb7a011245e7b8428d1615a9e755v.jpg)

![点击后](https://ae01.alicdn.com/kf/H56ac52b1ea1e4defb993c9030463d9d8T.jpg)

打开 `themes/matery/layout/layout.ejs`，在对应位置添加如下代码：

    <script type="text/javascript">
        var OriginTitile = document.title,
            st;
        document.addEventListener("visibilitychange", function () {
            document.hidden ? (document.title = "点击前的文字", clearTimeout(st)) : (document.title =
                "点击后的文字", st = setTimeout(function () {
                    document.title = OriginTitile
                }, 3e3))
        })
    </script>

>记得先 `hexo clean` 再 `hexo g` ，防止出错.

### 3、修改主题颜色

在主题文件的 `/source/css/matery.css` 文件中，搜索 `.bg-color` 来修改背景颜色：

    /* 整体背景颜色，包括导航、移动端的导航、页尾、标签页等的背景颜色. */
    .bg-color {
        background-image: linear-gradient(to right, #4cbf30 0%, #0f9d58 100%);
    }

    @-webkit-keyframes rainbow {
    /* 动态切换背景颜色. */
    }

    @keyframes rainbow {
        /* 动态切换背景颜色. */
    }

### 4、谷歌 SEO 

#### （1）SEO 定义

`SEO`（Search Engine Optimization）即搜索引擎优化，

维基百科上给出的定义如下：

>搜索引擎优化是一种通过了解搜索引擎的运作规则来调整网站，以及提高目的网站在有关搜索引擎内排名的方式。

SEO 可从两方面入手：

- 1.技术手段：

    通过研究搜索引擎的规则，利用某些技巧提升 SEO 效果；

- 2.内容质量：

    内容质量是更长久的提升SEO效果的核心，这里直接引用维基百科中的内容：

    >站点经常地更新，有用、原创的内容，和创建几个实用、有意义的导入链接，获得相当可观数目的基本搜索流量不是什么难事。

    >当站点拥有有用的内容，其它站点员自然而然会链接至该站，进而增加访客它的网页级别和访客流。当访客发现一个有用的网站，他们倾向于利用电子邮件或者及时消息链接介绍给其它访客。

    >总括来说，增进网站质量的搜索引擎优化实现很可能比直接查找操控搜索排名手段的短期实现要活得长久。顶尖的搜索引擎优化员们找寻的目标与搜索引擎追求发扬光大的东西二者不约而同。他们是：相关性、对他们用户有用的内容。换句话说，即向用户提供优质有用，而且独特的数据，以内容营销的方法，软性地吸引潜在的客户，自自然然地找到你的网页。

#### （2）验证网站

##### 查看

打开谷歌搜索，在搜索框里输入自己的博客 URL

    site: qinnian.xyz

如果提示说：

    找不到和您查询的 site: qinnian.xyz

说明未被收录。

我遇到的情况是谷歌是自动收录了，可能之前做过百度的SEO，虽然没有成功，但是配置了些乱七八糟的东西。如图：

![谷歌查询](https://ae01.alicdn.com/kf/Hdf96c6528b3b453893b0403b4c15baf2b.jpg)

##### 提交

若未被谷歌收录，则需在谷歌搜索进行配置。前往 [Google Search Console](https://search.google.com/search-console?resource_id=sc-domain%3Aqinnian.xyz)，登录谷歌账号。

添加属性，将博客地址 `site:https://qinnian.xyz/` 添至相应位置。

![域名解析](https://ae01.alicdn.com/kf/Hf8e077db0a0e424c846c9e5e985ada4c0.jpg)

谷歌搜索有多种验证方式，这里我选择的是腾讯域名解析。（这个步骤不多解释了，和前面添加域名一样）

![成功登录](https://ae01.alicdn.com/kf/H58422a8124394b4eb87c10f575277313n.jpg)

##### 添加

添加站点地图作用是告诉搜索引擎你的网站结构等信息，让搜索引擎更智能抓取内容。

- 第一步

    打开 `Git`，进入到根目录，输入如下命令安装：

        $ npm install hexo-generator-sitemap --save
- 第二步

    打开 Hexo 目录下的 _config.yml 文件，在最下方添加如下字段：

        # 自动生成sitemap
        sitemap:
        path: sitemap.xml

    重新编译：

        $ hexo generate

    重新部署：

        $ hexo deploy

- 第三步：

    进入 Google Search Console - 抓取 - 站点地图，点击「添加/测试站点地图」，输入你的博客网址。若无报错则站点地图提交成功

    ![无错误提示](https://ae01.alicdn.com/kf/Hbb406baaf56e4597893c3b4f5e05bf50S.jpg)

#### （3）提升排名

##### 关键字

博客根目录 `_config.yml` 文件进行如下修改，关键字英文逗号隔开：

    # Site
    title: 网站名称
    description: 网站描述
    author: 作者姓名
    subtitle: 作者简介
    language: zh-CN
    timezone:
    keywords: Web,HTML # 博客关键字
    
文章中加入关键字：

    ---
    title: ###
    date: ###
    categories: ###
    tags: ###
    keywords: ###
    description: ###
    ---


##### 路径简化

`Hexo` 默认的文章链接形式为 `domain/year/month/day/postname`，默认就是一个四级 `url`，并且可能造成 `url` 过长，对搜索引擎是十分不友好的。我们可以改成 `domain/postname` 的形式。编辑站点 `_config.yml` 文件，修改其中的 `permalink` 字段改为：

    permalink: :title.html

![路径简化](https://ae01.alicdn.com/kf/H2ad1dd960f8446f5a87b62aa480f6089n.jpg)

![效果展示](https://ae01.alicdn.com/kf/Hd7ea88a6c8b24bdaaee9851f89193b7aM.jpg)

#### （4）网站监测

登录谷歌站长管理平台 [Google Search Console](https://search.google.com/search-console/)

> 关于“科学上网的方式”，这里不作分享

![Google Search Console 效果](https://pic2.superbed.cn/item/5de87735f1f6f81c50b8522d.jpg)

再次搜索我的网站地址：

    site: qinnian.xyz

![谷歌SEO](https://pic1.superbed.cn/item/5de8a8bef1f6f81c50c0d8f2.jpg)

这边可以对比一下百度搜索的效果

>提交链接并且站点被百度收录估计要花一个月的时间，额！所以我暂时先搁置了。

![百度SEO](https://pic1.superbed.cn/item/5de8a94ff1f6f81c50c12492.jpg)

### 5、网站加载速度优化

#### （1）网站测速

在浏览谷歌网站过程中，发现了几个网站测速工具：

- [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
    
    >`Google PageSpeed Insights` 一款可以分析网页速度瓶颈谷歌浏览器插件

    - 手机端评分 52 分

    ![手机版](https://pic2.superbed.cn/item/5de8b032f1f6f81c50c28d28.jpg)
    ![移动优化建议](https://pic.superbed.cn/item/5de8b0c2f1f6f81c50c2a669.jpg)

    - 电脑端评分 89 分
    ![电脑版](https://pic.superbed.cn/item/5de8b056f1f6f81c50c29383.jpg)

    ![桌面优化建议](https://pic2.superbed.cn/item/5de8b07ff1f6f81c50c29a3f.jpg)

- [Pingdom](https://tools.pingdom.com/)
    >`pingdom`全面的网站监测服务网站,可测速和ping跟踪路由,可以免费监测1个站点,最短1分钟监测一次。

    网页评测 71 分
    ![Pingdom 测试](https://pic2.superbed.cn/item/5de8b298f1f6f81c50c30a04.jpg)

- [GTmetrix](https://gtmetrix.com/) 
    
    >`GTmetrix` 主要优点在于提供了丰富的详细的测量结果，并建议如何来优化网页中每个元素的，最重要的是会根据网站的具体情况，直接告诉你导致网站加载速度变慢的根源在哪里

    ![GTmetrix 测试](https://pic3.superbed.cn/item/5de8b5e8f1f6f81c50c38cc0.jpg)

>综上，我的网站加载速度慢的原因为：
>
>1、服务器不稳定速度慢
>
>>我使用的是`GitHub`代替服务器，`GitHub`本身就是国外的，在浏览速度确实比不上国内网站。于是我想，如果利用 `github pages` 和 `coding pages` 双部署是不是可以解决这个问题。未来可以考虑选择大的空间服务商,买最好的云服务。
>
>2、站点存在大量的JS调用：
>
>>当站点上有太多的JS调用时，它将增加页面响应时间，因为访问者在访问站点时将增加JS程序调用的响应时间。精简代码是个不错的选择，所以我选择了 `Gulp` 实现代码压缩。
>
>3、站点图片大，图片外链多
>
>>图片加载时间是造成网站访问速度慢的最大因素。这一点，当初建站的时候就已经意识到这个问题。
>
>>所以我就把网站图片存储到第三方空间。之前用国外的 [SMMS图床](https://sm.ms/) ,现在用国内的 [聚合图床](https://www.superbed.cn/) 。相对而言还是建议用国内的图床，访问速度更快些。
>
>>如果是重要图片尽量上传到自己空间，以免外链发生错误图片无法显示。外链图片速度很慢肯定是影响网站打开速度的，建议减少数量。(未来我准备在GitHub 建一个仓库自己做图床，这样最保险)

#### （2）图片懒加载

##### 前言

例如我这篇博客，如果一个页面的图片很多，那么如何来提高博客的访问速度呢？

懒加载，通俗点讲就是当你翻到图片的时候再加载那张图片，而不是以下将本页面的所有图片都加载完。

##### 配置

参照开源仓库：[hexo-lazyload-image](https://github.com/Troy-Yang/hexo-lazyload-image)

在你的 `Blog` 目录下，执行以下命令：

    npm install hexo-lazyload-image --save

然后在你的 `Blog` 目录的配置文件 `_config.yml`  中添加配置:

    lazyload:
      enable: true
      onlypost: false
      loadingImg: ./medias/loading.gif

>onlypost
>
>>是否仅文章中的图片做懒加载, 如果为 `false`, 则主题中的其他图片, 也会做懒加载, 如头像, `logo` 等任何图片。

>loadingImg  图片未加载时的代替图
>
>>不填写使用默认加载图片, 如果需要自定义，添填入 `loading` 图片地址，如果是本地图片，不要忘记把图片添加到你的主题目录下。`Matery`主题需将图片放到 `\themes\Matery\source\medias` 目录下, 然后引用时: `loadingImg: ./medias/图片文件名`

到这“图片懒加载”就完成了！截图如下



![loading 效果图](https://pic1.superbed.cn/item/5de8e4f5f1f6f81c50ccccd1.jpg)

#### （3）Gulp实现代码压缩

>安装 `Gulp` 过程中，使用 `npm` 进行安装，结果出现了各种 `err` 异常，估计是被。。墙了，这里推荐使用国内镜像解决这个问题。

    #淘宝镜像
    npm config set registry https://registry.npm.taobao.org  

首先我们需要安装Gulp插件和功能模块

    #安装gulp
    npm install gulp --save  

![安装 gulp 结果](https://pic3.superbed.cn/item/5de8eb8cf1f6f81c50cf4654.jpg)

    # 安装功能模块
    npm install gulp-htmlclean gulp-htmlmin gulp-minify-css gulp-uglify gulp-imagemin --save

![安装功能模块](https://pic3.superbed.cn/item/5de8f139f1f6f81c50d116b8.jpg)

    # 额外的功能模块
    npm install gulp-debug gulp-clean-css gulp-changed gulp-if gulp-plumber gulp-babel babel-preset-es2015 del --save

![安装额外的功能模块](https://pic3.superbed.cn/item/5de8f139f1f6f81c50d116b8.jpg)

接下来在博客的根目录下新建gulpfile.js文件，并复制下面的内容到文件中。

    var gulp = require("gulp");
    var debug = require("gulp-debug");
    var cleancss = require("gulp-clean-css"); //css压缩组件
    var uglify = require("gulp-uglify"); //js压缩组件
    var htmlmin = require("gulp-htmlmin"); //html压缩组件
    var htmlclean = require("gulp-htmlclean"); //html清理组件
    var imagemin = require("gulp-imagemin"); //图片压缩组件
    var changed = require("gulp-changed"); //文件更改校验组件
    var gulpif = require("gulp-if"); //任务 帮助调用组件
    var plumber = require("gulp-plumber"); //容错组件（发生错误不跳出任务，并报出错误内容）
    var isScriptAll = true; //是否处理所有文件，(true|处理所有文件)(false|只处理有更改的文件)
    var isDebug = true; //是否调试显示 编译通过的文件
    var gulpBabel = require("gulp-babel");
    var es2015Preset = require("babel-preset-es2015");
    var del = require("del");
    var Hexo = require("hexo");
    var hexo = new Hexo(process.cwd(), {}); // 初始化一个hexo对象

    // 清除public文件夹
    gulp.task("clean", function() {
    return del(["public/**/*"]);
    });

    // 下面几个跟hexo有关的操作，主要通过hexo.call()去执行，注意return
    // 创建静态页面 （等同 hexo generate）
    gulp.task("generate", function() {
    return hexo.init().then(function() {
        return hexo
        .call("generate", {
            watch: false
        })
        .then(function() {
            return hexo.exit();
        })
        .catch(function(err) {
            return hexo.exit(err);
        });
    });
    });

    // 启动Hexo服务器
    gulp.task("server", function() {
    return hexo
        .init()
        .then(function() {
        return hexo.call("server", {});
        })
        .catch(function(err) {
        console.log(err);
        });
    });

    // 部署到服务器
    gulp.task("deploy", function() {
    return hexo.init().then(function() {
        return hexo
        .call("deploy", {
            watch: false
        })
        .then(function() {
            return hexo.exit();
        })
        .catch(function(err) {
            return hexo.exit(err);
        });
    });
    });

    // 压缩public目录下的js文件
    gulp.task("compressJs", function() {
    return gulp
        .src(["./public/**/*.js", "!./public/libs/**"]) //排除的js
        .pipe(gulpif(!isScriptAll, changed("./public")))
        .pipe(gulpif(isDebug, debug({ title: "Compress JS:" })))
        .pipe(plumber())
        .pipe(
        gulpBabel({
            presets: [es2015Preset] // es5检查机制
        })
        )
        .pipe(uglify()) //调用压缩组件方法uglify(),对合并的文件进行压缩
        .pipe(gulp.dest("./public")); //输出到目标目录
    });

    // 压缩public目录下的css文件
    gulp.task("compressCss", function() {
    var option = {
        rebase: false,
        //advanced: true,               //类型：Boolean 默认：true [是否开启高级优化（合并选择器等）]
        compatibility: "ie7" //保留ie7及以下兼容写法 类型：String 默认：''or'*' [启用兼容模式； 'ie7'：IE7兼容模式，'ie8'：IE8兼容模式，'*'：IE9+兼容模式]
        //keepBreaks: true,             //类型：Boolean 默认：false [是否保留换行]
        //keepSpecialComments: '*'      //保留所有特殊前缀 当你用autoprefixer生成的浏览器前缀，如果不加这个参数，有可能将会删除你的部分前缀
    };
    return gulp
        .src(["./public/**/*.css", "!./public/**/*.min.css"]) //排除的css
        .pipe(gulpif(!isScriptAll, changed("./public")))
        .pipe(gulpif(isDebug, debug({ title: "Compress CSS:" })))
        .pipe(plumber())
        .pipe(cleancss(option))
        .pipe(gulp.dest("./public"));
    });

    // 压缩public目录下的html文件
    gulp.task("compressHtml", function() {
    var cleanOptions = {
        protect: /<\!--%fooTemplate\b.*?%-->/g, //忽略处理
        unprotect: /<script [^>]*\btype="text\/x-handlebars-template"[\s\S]+?<\/script>/gi //特殊处理
    };
    var minOption = {
        collapseWhitespace: true, //压缩HTML
        collapseBooleanAttributes: true, //省略布尔属性的值  <input checked="true"/> ==> <input />
        removeEmptyAttributes: true, //删除所有空格作属性值    <input id="" /> ==> <input />
        removeScriptTypeAttributes: true, //删除<script>的type="text/javascript"
        removeStyleLinkTypeAttributes: true, //删除<style>和<link>的type="text/css"
        removeComments: true, //清除HTML注释
        minifyJS: true, //压缩页面JS
        minifyCSS: true, //压缩页面CSS
        minifyURLs: true //替换页面URL
    };
    return gulp
        .src("./public/**/*.html")
        .pipe(gulpif(isDebug, debug({ title: "Compress HTML:" })))
        .pipe(plumber())
        .pipe(htmlclean(cleanOptions))
        .pipe(htmlmin(minOption))
        .pipe(gulp.dest("./public"));
    });

    // 压缩 public/uploads 目录内图片
    gulp.task("compressImage", function() {
    var option = {
        optimizationLevel: 5, //类型：Number  默认：3  取值范围：0-7（优化等级）
        progressive: true, //类型：Boolean 默认：false 无损压缩jpg图片
        interlaced: false, //类型：Boolean 默认：false 隔行扫描gif进行渲染
        multipass: false //类型：Boolean 默认：false 多次优化svg直到完全优化
    };
    return gulp
        .src("./public/medias/**/*.*")
        .pipe(gulpif(!isScriptAll, changed("./public/medias")))
        .pipe(gulpif(isDebug, debug({ title: "Compress Images:" })))
        .pipe(plumber())
        .pipe(imagemin(option))
        .pipe(gulp.dest("./public"));
    });
    // 执行顺序： 清除public目录 -> 产生原始博客内容 -> 执行压缩混淆 -> 部署到服务器
    gulp.task(
    "build",
    gulp.series(
        "clean",
        "generate",
        "compressHtml",
        "compressCss",
        "compressJs",
        "compressImage",
        gulp.parallel("deploy")
    )
    );

    // 默认任务
    gulp.task(
    "default",
    gulp.series(
        "clean",
        "generate",
        gulp.parallel("compressHtml", "compressCss", "compressImage", "compressJs")
    )
    );
    //Gulp4最大的一个改变就是gulp.task函数现在只支持两个参数，分别是任务名和运行任务的函数

最后 `hexo clean` && `hexo g` && `gulp` && `hexo d` 就可以了

>注意，很可能你会运行到第三步，也就是运行gulp压缩命令时会报错，如图所示：

![错误](https://pic1.superbed.cn/item/5de8f5c7f1f6f81c50d22b40.jpg)

那是因为gulp安装的本地版本和hexo自带的版本不对应导致，第三步gulp压缩可以用下面命令强制使用本地版本：

    node ./node_modules/gulp/bin/gulp.js

![gulp 成功](https://pic1.superbed.cn/item/5de8f61cf1f6f81c50d23c80.jpg)

#### （4）github 和 coding 双部署

>部署到 `Coding Pages` 的好处：国内访问速度更快，可以提交百度收录
>
>因为`GitHub` 禁止了百度的爬取
>
>问题来了！！！
>
>我是不是又要重新写配置步骤？懒了，还是简单描述一下过程吧！

##### A、创建项目

 [Coding 官网](https://coding.net/)点击个人版登陆，没有账号就注册一个并登录，由于 `Coding` 已经被腾讯收购了，所以登录就会来到腾讯云开发者平台，点击创建项目。

 项目名称建议和你的用户名一致，这样做的好处是：到时候可以直接通过 `user_name.coding.me` 访问你的博客，如果项目名与用户名不一致，则需要通过 `user_name.coding.me/project_name` 才能访问，项目描述可以随便写。

 ##### B、配置公钥

 配置 `SSH` 公钥方法与 `GitHub Pages` 的方式差不多，点击你的头像，依次选择`【个人设置】-【SSH公钥】-【新增公钥】`

 前面部署到 `GitHub Pages` 的时候就已经有了一对公钥，我们直接将该公钥粘贴进去就行，公钥名称可以随便写，选中永久有效选项。

>PS：公钥储存位置一般在 `C:\Users\用户名\.ssh` 目录下的 `id_rsa.pub` 文件里，用记事本打开复制其内容即可

添加公钥后，我们可以右键 `Get Bash`，输入以下命令来检查是否配置成功：

    ssh -T git@git.coding.net

![成功配置](https://pic.superbed.cn/item/5de8ff99f1f6f81c50d48d18.jpg)

##### C、配置 _config.yml

进入你的项目，在右下角有选择连接方式，选择 `SSH` 方式（`HTTPS` 方式也可以，但是这种方式有时候可能连接不上，`SSH` 连接不容易出问题），一键复制，然后打开你本地博客根目录的 `_config.yml` 文件，找到 `deploy` 关键字，添加 `coding` 地址：`coding: git@git.dev.tencent.com:user_name/user_name.git`，也就是刚刚复制的 `SSH` 地址。

![找到 `coding` 地址](https://pic2.superbed.cn/item/5de901f8f1f6f81c50d5133c.jpg)

![添加 `coding` 地址](https://pic3.superbed.cn/item/5de902bcf1f6f81c50d5380c.jpg)

添加完成后先执行命令 `hexo clean` 清理一下缓存，然后执行命令 `hexo g -d` 将博客双线部署到 `Coding Pages` 和 `GitHub Pages`，如下图所示表示部署成功：

![配置 _config.yml 成功](https://pic3.superbed.cn/item/5de903c6f1f6f81c50d57ba9.jpg)

##### D、开启 Coding Pages

进入你的项目，在代码栏下选择 `Pages` 服务，一键开启 `Coding Pages`，等待几秒后刷新网页即可看到已经开启的 `Coding Pages`，到目前为止，你就可以通过 `xxxx.coding.me`（比如我的是 `qinnian.coding.me` ）访问你的 `Coding Pages` 页面了

![Coding Pages](https://pic3.superbed.cn/item/5de90467f1f6f81c50d59aee.jpg)

##### E、绑定域名

首先在你的域名 `DNS` 设置中添加一条 `CNAME` 记录指向 `xxxx.coding.me`，解析路线选择默认，将 `GitHub` 的解析路线改为境外，这样境外访问就会走 `GitHub`，境内就会走 `Coding`，也有人说它是智能解析，自动分配路线，如果解析路线都是默认，境外访问同样会智能选择走 `GitHub`，境内走 `Coding`，我没有验证过，有兴趣的可以自己试试。

然后点击静态 `Pages` 应用右上角的设置，进入设置页面，这里要注意，如果你之前已经部署到了 `GitHub Pages`并开启了 `HTTPS`，那么直接在设置页面绑定你自己的域名，`SSL/TLS` 安全证书就会显示申请错误，如下图所示，没有申请到 `SSL` 证书，当你访问你的网站时，浏览器就会提示不是安全连接。

![错误提示](https://pic2.superbed.cn/item/5de90dcdf1f6f81c50d7bca8.jpg)

>申请错误原因是：在验证域名所有权时会定位到 Github Pages 的主机上导致 SSL 证书申请失败
>
>正确的做法是：先去域名 `DNS` 把 `GitHub` 的解析暂停掉，然后再重新申请 `SSL` 证书，大约十秒左右就能申请成功，然后开启强制 `HTTPS` 访问

这里也建议同时绑定有 `www` 前缀和没有 `www` 前缀的，然后设置其中一个为【首选】，另一个设置【跳转至首选】，这样不管用户是否输入 `www` 前缀都可以访问了

在博客资源引用的时候也要注意所有资源的 URL 必须是以 https:// 开头，不然浏览器依旧会提示不安全！

![成功](https://pic3.superbed.cn/item/5de915bbf1f6f81c50d95c3f.jpg)


##### D、查看效果

![qinnian.coding.me](https://pic2.superbed.cn/item/5de91a9cf1f6f81c50da399e.jpg)

![qinnian.github.io](https://pic3.superbed.cn/item/5de91b28f1f6f81c50da502c.jpg)

至此，我们的 Hexo 博客就成功双线部署到 `Coding Pages` 和 `GitHub Pages` 了！