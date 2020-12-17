---
layout:     post
title:      服务器使用指南
subtitle:   安装、常见命令
date:       2020-12-17
updated:    2020-12-17
author:     Jing Yang
stickie:    false
header-img: img/scene8.jpg
catalog: true
tags:
    - Collection	
---

## 服务器

ssh连接

```
ssh username@ip****** -p 端口号
```

添加用户：

```
sudo adduser username
```

赋予用户root权限：

```
sudo usermod -aG sudo username
```

系统中已经有python 3.8.2

由于服务器重装过，以前在本地或者vscode用过此服务器的人需要在C盘/用户/username/.ssh/known_hosts中将相应记录删掉才能重新使用vscode登录。xshell则不需要如此做。

安装pip和更新

```
sudo apt install python3-pip
```

安装numpy或者其他库

```
pip3 install numpy(scipy/matplotlib...)
```

## 安装Matlab

首先在matlab官网下载matlab 2020b

[Matlab 2020b]: https://www.mathworks.com/downloads/web_downloads/download_release?release=R2020b

将压缩包放入服务器后，通过命令解压到新建的matlab文件夹

```
mkdir matlab
unzip -q matlab_R2019b_glnxa64.zip -d matlab
```

进入matlab文件夹并运行install

```
cd matlab
./install # 不要加sudo，否则会报错，相应的由于没有权限故安装目录必须选在自己文件夹内
```

安装激活过程和在自己电脑上安装matlab没有区别，安装目录可选在自己文件夹下。（安装在root目录下会出现一点问题，暂时还没找到方法解决）

安装过程中需要登录mathlab的账号，选择账号中相应的许可证书即可。

现在我已经在我的目录下安装好了R2020b版本，只需要对每个用户进行激活即可。

对于服务器新用户，输入以下命令

```
cd /home/jingyang/R2020b/bin
./activate_matlab.sh
```

将会弹出matlab激活程序，需要输入带有许可证的mathwork账户。（如果没有，可以暂时向荆洋要）

选择相应许可证后即可成功打开matlab。

需要运行matlab时候输入以下命令

```
cd /home/jingyang/R2020b/bin
./matlab
```

如果嫌每次输入麻烦的话，每个用户可以执行以下操作：

```
vi ~/.bashrc
```

进入后摁`i`进入insert模式 加入以下代码：

```
alias matlab='/home/jingyang/R2020b/bin/matlab'
```

摁`esc`退出insert模式，输入 `:wq!` 保存改动并退出，并在命令行激活该改动

```
source ~/.bashrc
```

以后每次只需要输入`matlab`即可激活程序。（该步骤仅对每个用户有用）

## 虚拟环境（重要）

需要强调一点的是不要随意在系统环境中直接升级、安装、卸载包，这可能会导致别人已有的依赖于系统环境的代码出现bug。最好的做法是每一个人为自己的环境创立一个虚拟环境，甚至可以对自己不同的项目创立不同的虚拟环境。

虚拟环境使您能够在服务器上为Python项目保留一个独立的空间，从而确保每个项目都有自己的一组依赖软件包，不会干扰任何其他项目。通过设置编程环境，我们可以更好地控制Python项目、以及管理不同版本的包。在使用第三方软件包时，这一点尤其重要。

你可以设置任意多数量的Python编程环境。每个环境简单来讲，就是服务器中的一个目录或文件夹，其中包含一些脚本以使其成为"环境"。

虽然有几种方法可以在Python中实现编程环境，我们将在这里使用**venv**模块，它是标准Python 3库的一部分。让我们输入以下命令来安装venv：

```
sudo apt install -y python3-venv
```

安装好venv之后，我们就可以创建环境了。我们可以将Python编程环境放某个已有的目录中，也可以使用`mkdir`创建一个新目录，如下所示：

```
mkdir environments
cd environments
```

当你进入希望安装环境群组的目录`environments`中之后，可以通过运行以下命令创建环境

```
python3 -m venv my_env
```

总的来说`pyvenv`将设置一个新目录`my_env`，其中包含一些项目，可以使用`ls`进行查看：

```
ls my_env
```

你需要激活环境才能使用它，你可以通过输入以下命令，调用**activate**激活脚本：

```
source my_env/bin/activate
```

现在命令行每行的行首提示，将以你的环境名作为前缀，在我们的情况下它被称为my_env。你的前缀可能看起来有些不同，但括号中的环境名称应该是在行首。

这个前缀让我们知道环境my env当前处于活动状态，这意味着当我们在这里创建程序时，它们将只使用这个特定环境的设置和包。

退出当前环境

```
deactivate
```

