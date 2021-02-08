

## 关于Linux

> Linux是一套免费使用和自由传播的类Unix操作系统，是一个基于POSIX和UNIX的多用户、多任务、支持多线程和多CPU的操作系统。
> Linux存在着许多不同的版本，但它们都使用了Linux内核。Linux可安装在各种计算机硬件设备中。
> Linux的基本思想有两点：第一，一切都是文件；第二，每个软件都有确定的用途。
> 发行版本 Ubuntu、RedHat、CentOS、Debian等
> 目前Linux 更多的是应用于服务器上，而桌面操作系统更多使用的是 Windows。

## Debian

> Debian 是一个自由的操作系统（OS），它还附带了超过 59000 个软件包，这些预先编译好的软件被打包成一种良好的格式以便于在您的机器上进行安装。
> 操作系统是使计算机运行的基本程序和工具的集合，其中最主要的部分称为内核（kernel）。内核是计算机中最重要的程序，负责一切基本的调度工作，并让您运行其他程序。Debian 系统目前采用 Linux 内核。

## Ubuntu

> Linux发行版（distro）。一个以桌面应用为主的开源GNU/Linux操作系统。
> Ubuntu有长期支持版本(Long Term Support，LTS)：Ubuntu12.04、14.04、16.04、18.04。
> 每个Ubuntu的版本代号都是按照“形容词+动物”的格式命名的。
> http://releases.ubuntu.com/16.04/ubuntu-16.04.6-desktop-amd64.iso

![image-20201214093534977](https://i.loli.net/2020/12/14/FBLPM2QJcnUIXg3.png)

***\*ROS\****

Ubuntu 16.04(xenial)和ROS kinetic版本

一个开源协议的开源软件。

ROS(Robot Operating System）是一个机器人软件平台，它能为异质计算机集群提供类似操作系统的功能。

ROS提供一些标准操作系统服务，ROS是一个适用于机器人的开源的元操作系统。它提供了操作系统应有的服务，它也提供用于获取、编译、编写、和跨计算机运行代码所需的工具和库函数。ROS 的主要目标是为机器人研究和开发提供代码复用的支持。

在线安装  https://wiki.ros.org/kinetic/Installation/Ubuntu

配置安装教程  https://blog.csdn.net/wangguchao/article/details/81044558

Linux系统命令工具基本知识 https://www.cnblogs.com/cokefentas/p/11101000.html

社区化软件库  xx-ros-pkg  wiki.ros.org/pal-ros-pkg

kinetic镜像  https://blog.csdn.net/zhangrelay/article/details/54632130

易科机器人小组  http://blog.exbot.net/

indigo镜像安装  http://blog.exbot.net/archives/818

---

对于纯的Python代码同时支持Python3和Python2.7是比较容易的，基本上ROS的代码也都是支持的。问题在于包含了C++或者C的那部分Python代码。Python2.7和Python3的c module代码相差很大。一次只能编译其中的一种版本。而且很多module没有做好Python3的支持。在Python3环境下也无法编译。这就是ROS无法支持Python3的原因

---

***\*Ubuntu学习\****

1,学习Linux命令行

通常我们在使用 Linux 时，不是直接与系统打交道，而是通过一个叫做 Shell 的中间程序来完成的，Linux 系统还提供了一个叫做终端模拟器的程序（Terminal）。  gnome-terminal.

基本操作

[Tab] 使用Tab键来进行命令补全

命令行中获取帮助

```
$ help
```

有趣的 Linux 命令，这一节介绍一个可以输出图形字符的命令banner

条幅 

```
$banner Linux
printerbanner -w 50 logo
```

跑火车 

```
sl 
```

古诗

```
sudo apt install fortune-zh   
fortune-zh #随机诗句
```

小松鼠 

```
oneko
```

在 Linux 系统里， root 账户拥有整个系统至高无上的权利，比如 新建/添加 用户。

```
sudo <>
```

---

***\*实验楼\**** ***\*教程\****

***\*实验 1 Hello，ShiYanLou!\**** 

终端下生成可执行文件，并执行

指定位置：cd /home/akingse/shiyanlou

新建文件：touch 1-1.c

使用git编辑器打开：gedit 1-1.c

输入代码：Ctrl+V

```
#include<stdio.h>

int main()

{   printf("Hello ShiYanLou!\n");   return 0;}
```

使用***\*gcc\****生成可执行文件：gcc -o 1-1 1-1.c #  gcc 1-1.c -o 1-1 #两种语法

gcc -o选项用来指定输出文件，它的用法为：gcc [infile] -o [outfile]

执行这个文件：./1-1 # 1-1 为可执行文件 (application/x-executable)

注释：

gcc是GUN Compiler Collection编译器集合。GNU是一个[自由](https://baike.baidu.com/item/自由)的[操作系统](https://baike.baidu.com/item/操作系统)，是GNU is Not Unix的[递归缩写](https://baike.baidu.com/item/递归缩写)。

gcc是一套由 GNU 开发的编程语言编译器，可以支持多种语言编译。

终端：Xfce终端，***\*gnome-terminal\****

代码编辑器：Vim，vscode，***\*gedit\****

IDE：集成开发环境，***\*RoboWare\****，VC，VS，Pycharm （第三方编译器）

---

***\*ubuntu\*******\*终端常用操作\****

指定当前的位置：

```
cd /home/akingse/shiyanlou
```

得到（旧计算机名） akingse@akingse-cw65s:~/shiyanlou$ 

新计算机名 akingse@cw65s-ubuntu

$是「命令提示符」，提示你：请在它后面输入命令。

查看当前目录下的文件和目录：ls

获取当前目录的绝对路径：pwd

新建一个名为 mycode 的目录：$ mkdir mycode

新建文件touch；复制cp;cp -r;剪切mv;删除rm -r;重命名mv;打印cat;

 

***\*cd\****

> 向前cd;后退 cd -;
>
> cd / #跳转到根目录，cw65s-ubuntu的C盘
>
> cd ~ #跳转到当前用户home/akingse 目录
>
> Ctrl+C 终止一个程序的运行，回到提示符下。
>
> Ctrl+X 复制文本。Ctrl+V 粘贴
>
> Ctrl+Z 暂停，挂起一个当前运行的程序
>
> Ctrl+D 退出当前的[SHELL](https://www.baidu.com/s?wd=SHELL&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)，相当于exit命令 
>
> Ctrl+L 清屏

![image-20201214094035166](https://i.loli.net/2020/12/14/cb5hrsvqHATGan2.png)![image-20201214094045906](https://i.loli.net/2020/12/14/pkH65O8WMNgjvLe.png)

终端创建 Python 文件并执行

```
cd /home/akingse/shiyanlou

gedit test.py

Ctrl+V print('hello shiyanlou!')

python3 test.py #用***\*python3执行\**** ***\*.py\*
```

***\*Git 与 GitHub\****

Git是目前最先进的版本控制工具，管理着地球上最庞大的代码仓库。

GitHub是全球最大的代码托管平台、开源社区。

sudo apt-get install git

创建文件：gedit README.md

查看文件内容：cat README.md

Git 的初始化操作，将文件夹置于 Git 的控制管理之下：git init

提交代码

1先创建本地文件；

2 git add 命令，将创建或修改的文件添加到本地的暂存区；

```
cd /home/akingse/shiyanlou/Demo

git add README.md
```

3 git commit 命令，提交文件到本地仓库；

```
git config --global user.name "akingse"

git config --global user.email "493412279l@qq.com"

git commit -m "first commit"
```

 

4 git push命令，将本地代码库同步到云仓库；

```
git remote add origin https://github.com/akingse/shiyanlou.git

git push origin master
```

克隆到本地 git clone [url]

---

