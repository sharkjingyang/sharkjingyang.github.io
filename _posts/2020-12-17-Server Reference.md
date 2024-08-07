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

## 服务器登录

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

系统中已经有自带python，推荐用户自己安装anaconda来管理库

## pytorch环境

目前服务器中已经安装了比较新的显卡驱动，理论上来说之前荆洋已经在根目录上安装了cuda和cudnn，用户只需要自行安装pytorch即可。

### 查看服务器使用情况

可以pip安装gpustat库后使用下述命令查看gpu使用情况

```
watch -n 1 -c gpustat --color
```

或者直接使用下述查看完整使用情况

```
nvidia-smi
```

### 使用tensorboard查看训练（optional）

在使用TensorBoard前，我们需要先指定一个文件夹供TensorBoard保存记录下来的数据。然后调用tensorboard中的SummaryWriter作为上述“记录员”

```python
from tensorboardX import SummaryWriter

writer = SummaryWriter('./runs')
```

上面的操作实例化SummaryWritter为变量writer，并指定writer的输出目录为当前目录下的"runs"目录。也就是说，之后tensorboard记录下来的内容都会保存在runs。

如果使用PyTorch自带的tensorboard，则采用如下方式import：

```python
from torch.utils.tensorboard import SummaryWriter
```

启动tensorboard也很简单，在命令行中输入

```python
tensorboard --logdir=/path/to/logs/ --port=xxxx
```

其中“path/to/logs/"是指定的保存tensorboard记录结果的文件路径（等价于上面的“./runs"，port是外部访问TensorBoard的端口号，可以通过访问ip:port访问tensorboard。

更具体的教程可以参考“：[tensorboard教程](https://datawhalechina.github.io/thorough-pytorch/%E7%AC%AC%E4%B8%83%E7%AB%A0/7.3%20%E4%BD%BF%E7%94%A8TensorBoard%E5%8F%AF%E8%A7%86%E5%8C%96%E8%AE%AD%E7%BB%83%E8%BF%87%E7%A8%8B.html)



## 安装Matlab

### 下载安装 

事实上荆洋已经在他的目录下安装了matlab R2020b和R2024b，只需要对每个用户进行激活即可（跳过到本教程激活步骤），当然也可以每个用户也可以在自己目录下安装matlab。以下为在自己目录下载安装matlab教程。

首先在matlab官网登录账号后下载matlab linux压缩安装包，以2020b为例

将压缩包放入服务器后，通过命令解压到新建的matlab_2020b文件夹

```
mkdir matlab_2020b
unzip -q matlab_R2020b_glnxa64.zip -d matlab_2020b
```

进入matlab_2020b文件夹并运行install

```
cd matlab_2020b
./install # 不要加sudo，否则会报错，相应的由于没有权限故安装目录必须选在自己文件夹内
```

安装激活过程和在自己电脑上安装matlab没有区别，安装目录可选在自己文件夹下。（安装在root目录下会出现一点问题，暂时还没找到方法解决）

安装过程中需要登录matlab的账号，选择账号中相应的许可证书即可。

### 激活

对于服务器新用户，输入以下命令

```
cd /home/jingyang/R2020b_matlab/bin
./activate_matlab.sh
```

如果你有可视化程序，那么将会弹出matlab激活程序，需要输入带有许可证的mathwork账户，选择相应许可证后即可成功打开matlab。

如果没有安装过可视化[Xshell](https://www.netsarang.com/en/xshell/)和[Xmanager](https://www.netsarang.com/en/xmanager/)，来激活matlab。下载Xshell和Xmanager成功后，在Xshell中登录服务器，输入上述命令，即可弹出激活程序。

![Xshell_Xmanager](\img\post_img\Guidance_server_1.png)

### 运行

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
alias matlab='/home/jingyang/R2020b_matlab/bin/matlab'
```

摁`esc`退出insert模式，输入 `:wq!` 保存改动并退出，并在命令行激活该改动

```
source ~/.bashrc
```

以后每次只需要输入`matlab`即可激活程序。（该步骤仅对每个用户有用）

或者可以直接输入下属命令无窗口运行代码文件

```
matlab -nodisplay -nosplash -nodesktop -r "run('your_code.m'); exit;"
```

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

## 使用screen命令离线跑程序

利用screen命令可以为不同的任务开不同的窗口，这个窗口之间是可以切换的，同时，窗口和你的会话连接基本上没有任何区别

这样你可以在开一个连接的时候同时干多件事情，并且在终端看得到运行过程的同时而不会由于断网而导致代码停止运行。其常用命令如下：

```
$screen -S jy       #创建一个名为jy的窗口
```

当你不想呆在这个窗口时，你可以通过快捷键Ctrl+a+D断开这个窗口的连接而回到连接会话界面。

```
$screen -ls #可以查看已创建的所有窗口
```

会出现如下界面：

```
user@ubuntu-Super-Server:~/code$ screen -ls
There are screens on:
	28475.ssd	(2017年11月27日 20时07分41秒)	(Detached)
	28113.yolo	(2017年11月27日 19时57分26秒)	(Detached
```

返回已有的窗口

```text
$screen -r jy #重新连接到jy窗口，显示其运行过程
```

如果想直接停止某个窗口任务的运行，可以直接通过杀死id的方式

```
$kill 28475 #终止ssd窗口对应任务的运行，同时杀死该窗口
```

# LLM工具

可以利用LLM工具辅助写代码、修改论文、搜索，以下为推荐的大模型：

Chatgpt：https://chat.openai.com/

Deepseek：https://www.deepseek.com/  快速，目前开源大模型第一名 

Kimi：https://kimi.moonshot.cn/  可处理pdf，在处理长文本方面具有一定优势 

上述三者都有免费版本



