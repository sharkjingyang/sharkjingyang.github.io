---
layout:     post
title:      利用 GitHub Pages 搭建个人博客
subtitle:   How to build a blog by using Github Pages (Not finished)
date:       2019-12-7
author:     Jing Yang
header-img: img/scene7.jpg
catalog: true
tags:
    - My articles	
---

# 利用 Github Pages 搭建个人博客

> 感谢 [Github·BY](https://github.com/qiubaiying/qiubaiying.github.io) 提供的模板
>
> 写这篇文章主要是记录一下自己建立自己这个博客的过程
>
> 对于 HTLM 文件的使用依然还在摸索中

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

到这里一个复制的个人主页就初步完成了，在浏览器内输入 `你的github用户名.github.io` 就能进入你自己的主页啦，效果如图。之后我将说明如何修改文件使得来完全修改成你自己的主页。

![1.PNG](http://ww1.sinaimg.cn/large/006EGaNZgy1g9osj52bqcj31gw0q01ky.jpg)

## 网站文件

### 主要文件

* `_config.yml` 是全局配置文件，主要是负责 HOME 页面的排版。
* `_posts` 是存放 markdown 文件的地方，也就是我们的文章。
* `img` 是存放照片的文件夹，主要存放背景图已经 blog 中的各种标识。（文章中的图片需要上传图床）
* `.html` 文件配置的是链接的相关页面，如 Tags 、About 等。

### 修改文件

假装大家已经学会了使用 Github Desktop ，并且已经将仓库 Clone 到了本地。

