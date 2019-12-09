---
layout:     post                                                     
title:      利用 GitHub Pages 搭建个人博客                            
subtitle:   How to build a blog by using Github Pages
date:       2019-12-7                                                 
author:     Jing Yang                                                 
header-img: img/scene7.jpg
catalog: true        
updated :   2019-12-9                                                  
tags:                                                                  
    - My articles	 
---

## 利用 GitHub Pages 搭建个人博客

> 感谢 [Github·BY](https://github.com/qiubaiying/qiubaiying.github.io) 提供的模板
>
> 写这篇文章主要是记录一下自己建立自己这个博客的过程
>
> 对于网页布局的设置依然还在摸索中

## 主页样式

电脑上的样子：

![1.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9osj52bqcj31gw0q01ky.jpg)

手机上的样子：

<img src="http://ww1.sinaimg.cn/large/006EGaNZgy1g9oskdde8qj30u01sz0zx.jpg" alt="2.jpg" style="zoom:25%;" />

## 搭建 Blog

### 注册 Github

我主要利用 [Github Pages](https://pages.github.com/) 来搭建网站，编辑 markdown 文件用 [Typora](https://www.typora.io/)，不过大家也可以用 [Sublime](https://www.sublimetext.com/) 来编辑所有文件。

首先你得拥有一个 [Github](https://github.com/) 账号，注册过程不再详细赘述，现在已经推出了 [Github Desktop](https://desktop.github.com/) ，可以不再用命令行进行操作了（请避免像我先学了一天 Git 指令，然后痛苦地发现有了客户端）。

### 使用 Github Pages

可以选择新建立一个仓库然后作为在 Settings 里添加 Github Pages。Github 提供了许多非常简易的模板。但是学习网站排版将会花费大量的时间。所以，鼓励像我一样刚开始学习撰写 Blog 的人，直接扒了别人的网站模板。

在 Github 中搜索 `sharkjingyang.github.io`,就可以发现我[ Blog的仓库](https://github.com/sharkjingyang/sharkjingyang.github.io)。

然后点击 Fork ，你就可以把我的所有文件都搬进你自己的仓库啦。进入 Fork 过来的仓库。

进入 Settings 

![3.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9pw77qzxej30sh0hit9p.jpg)

 将仓库名 `sharkjingyang.github.io` 修改为 `你的github用户名.github.io` 。

![4.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9pw8hy2awj30sh0gaq48.jpg)

到这里一个复制的个人主页就初步完成了，在浏览器内输入 `你的github用户名.github.io` 就能进入你自己的主页啦，效果如图。之后我将说明如何修改文件使得完全修改成你自己的主页。

![1.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9osj52bqcj31gw0q01ky.jpg)

## 网站构成

### 主要文件

* `_config.yml` 是全局配置文件，主要是负责 HOME 页面的排版。
* `_posts` 是存放 markdown 文件的地方，也就是我们的文章。
* `img` 是存放照片的文件夹，主要存放背景图已经 blog 中的各种标识。（文章中的图片需要上传图床）
* `.html` 文件配置的是链接的相关页面，如 Tags 、About 等。

### 修改 HOME 主页

假装大家已经学会了使用 Github Desktop ，并且已经将仓库 Clone 到了本地。

首先我们来修改 `_config.yml` 文件，这是主页的全局配置文件。用 Sublime 打开，修改相关项完成对主页信息的编辑。

![5.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9pwqma4pjj30oi054jrt.jpg)

接下里我们修改侧边栏，可以加入自己的基本信息和照片。

![6.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9pwsdammaj30m302ijrc.jpg)

修改的就是这块，效果如图所示

![7.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9pwti2m25j307q06ztap.jpg)

修改侧边栏和网页底部的社交账号

![9.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9pwxfg322j30al032a9x.jpg)

![8.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9q2jztatyj30jq03vdfu.jpg)

这里要强调的是，username 填的并不是自己的用户名，而是个人主页网址的最后一部分。如我 instagram 的个人主页是 `https://www.instagram.com/shark_jing/`， 那么我填入的是 `shark_jing`。这是由于我们点击社交账号所导航到的是个人主页，而有些网站并不是以用户名作为结尾的。想要修改或者增加社交账号的相关路径，页脚的路径可修改 `footer.html` 文件，侧边栏可修改 `page.html` 文件。

当你修改完以上内容后，你的 HOME 主页就已经修改好了，接下来让我来看下如何写自己的文章。

## 写文章

网站的文章统一放在 `_posts` 文件夹内，采用 markdown 的格式。

每一篇文章的命名格式为 `2019-12-8-文章题目.md` 时间+标题的形式。

Markdown 是一种非常简单的标记语言，其目的就是为了把写文章的人从排版等繁琐的格式中解放出来。网上有很多 Markdown 的编辑器，常见的有 [Typora](https://www.typora.io/)、[马克飞象](https://maxiang.io/)、[MarkdownPad](http://markdownpad.com/)、Windows 商店里的 BookPad 等等，当然 [Sublime](https://www.sublimetext.com/) 添加插件以后也是可以编辑的。经过尝试，我个人比较喜欢用的是 Typora、马克飞象、BookPad 。不过秉承着免费、好用、个性化的原则，我在这里隆重安利 Typora。在这里引用一篇讲解 Typora 好处的文章给大家，详细解释了 Typora 的个性化以及方便性（[Typora 完全使用详解](https://sspai.com/post/54912)），Typora 直接渲染的功能可能对习惯 Latex 分屏的用户刚开始不太习惯，但是个性化的制定确实比其他 Markdown 编辑器高出一个档次。

关于 Markdown 的语法，花半个小时就能学习一下，再不济 Typora 顶栏也有完整的操作选项，这里是一篇有关 Markdown 语法的文章（[Markdown 基本语法](https://www.jianshu.com/p/191d1e21f7ed)）。

每篇文章的开头有这样一部分，是用来添加这篇文章的信息的。博客中文章将按照这里的时间进行排序。

![10.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9q3cfofirj30j105gdg0.jpg)

关于文章里的图片，不能直接从本地上传链接，否则会显示失败。解决方案是先将图片上传到图床，获取 URL 链接并用此链接插入图片。我用的是 [Chrome 的微博图床插件](https://chrome.google.com/webstore/detail/%E6%96%B0%E6%B5%AA%E5%BE%AE%E5%8D%9A%E5%9B%BE%E5%BA%8A/fdfdnfpdplfbbnemmmoklbfjbhecpnhf?utm_source=chrome-ntp-icon)上传图片。

到这里你就可以正式愉快的写文章啦！

## 其他文件修改

### About Me

这里我们想修改 About Me 的自我介绍页面，也就是侧边栏和右上角链接的页面。

![11.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9qwiroz91j31go0q5kjm.jpg)

打开 `about.html` 文件，可修改最上方几项来更换背景、标题、描述。

![12.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9qwl16n8aj30c202yglh.jpg)

接下来的内容是用 HTML 语言编辑的，这里我们先抛开页面排版的问题，可以略微学习一些简单的文字排版指令，来修改自我介绍页面文字内容，这是一篇讲述如何换行、列表等基础指令的文章。（ [HTML基础语法](https://www.jianshu.com/p/5892747102e7)）

### Index

打开 `index.html` 文件，这个文件主要涉及的是 Home 页的标语和文章的显示。

![14.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9qwt129eij311z07c7nm.jpg)

![15.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9qwto9rt1j30q1062jrs.jpg)

其对应的代码分别为：

![16.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9qww2lq70j30oz0290sk.jpg)

![17.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9qwwzjoxjj30v00alwet.jpg)

要说明的是 `post.date` 对应的是 Markdown 文件中开头填写的日期，而非文件名的日期，页面也将会按照该日期进行排列。`date: "%B %-d, %Y"` 是日期的显示格式。

### Tags

Tags 页面在 `tags.html` 文件中修改，不建议做大改动。

### Head

倘若要修改网站图标和手机上显示的网站图标

![18.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9qx5lzfucj306y011we9.jpg)

可在 `img` 文件夹中替换 `favicon.ico` 与 `apple-touch-icon.png`。或者可进入 `head.html` 文件，修改图片路径。

![19.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9qxbypb6rj30kb02kt8m.jpg)

## 写在最后

记得在 Github Desktop 中 commit 和 push origin 哦，再过一会儿刷新 `你的用户名.github.io` 就可以看到你的主页啦。

恭喜你拥有了自己的 Blog ！还不快写起文章来 ！



