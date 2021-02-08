## 基础配置

[引用](https://blog.csdn.net/r1141207831/article/details/106327172)
安装VNC、teamviewer方便，无屏控制；
使用sudo passwd设置root密码 
输入sudo -s 转为root用户
更新源和系统使用下面三个命令：

（修改软件源,注意对应版本 arm64-Focal 查看$ lsb_release -c）

---

## 树莓派4B安装Ubuntu mate 20.04

[引用](https://www.cnblogs.com/Biiigwang/p/11742893.html)

```shell
sudo gedit /etc/apt/sources.list
```

添加

```text
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-updates main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-updates main restricted universe multiverse

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-security main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-security main restricted universe multiverse

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial-backports main restricted universe multiverse

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial main universe restricted
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports/ xenial main universe restricted
```

阿里源

```
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
```

Ubuntu版本

| 16.04 | Xenial Xerus (好客的非洲地松鼠)      | 2016年4月 （LTS） |
| ----- | ------------------------------------ | ----------------- |
| 16.10 | Yakkety Yak（牦牛）                  | 2016年10月        |
| 17.04 | Zesty Zapus(开心的跳鼠)              | 2017年4月         |
| 17.10 | Artful Aardvark(机灵的土豚)          | 2017年10月        |
| 18.04 | Bionic Beaver（仿生海狸）            | 2018年4月(LTS)    |
| 18.10 | Cosmic Cuttlefish (宇宙般大小的乌贼) | 2018年10月        |
| 19.04 | Disco Dingo                          | 2019年4月         |
| 19.10 | Eoan Ermine                          | 2019年10月        |
| 20.04 | Focal Fossa                          |                   |

```shell
sudo apt update && sudo apt upgrade
```



---

#### 清华源 20.04-focal-ports (mate版本)

```
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal main restricted
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal main restricted

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-updates main restricted
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-updates main restricted

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal universe
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal universe
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-updates universe
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-updates universe

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-updates multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-updates multiverse

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-backports main restricted universe multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-backports main restricted universe multiverse

deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-security main restricted
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-security main restricted
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-security universe
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-security universe
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-security multiverse
deb-src http://mirrors.tuna.tsinghua.edu.cn/ubuntu-ports focal-security multiverse
```

```powershell
sudo apt-get update #更新源列表
sudo apt-get upgrade #更新已经安装的包
sudo apt-get dist-upgrade #更新软件，升级系统
```

Ubuntu 16.04 -- Xenial Xerus -- ROS Kinetic
Ubuntu 20.04 -- Focal Fossa -- ROS Noetic
[官网安装教程](https://wiki.ros.org/noetic/Installation/Ubuntu)

---

[引用](https://blog.csdn.net/r1141207831/article/details/106327172)
2.1添加软件源

```shell
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo sh -c '. /etc/lsb-release && echo "deb http://mirrors.tuna.tsinghua.edu.cn/ros/ubuntu/ `lsb_release -cs` main" > /etc/apt/sources.list.d/ros-latest.list'
```

添加key

```shell
sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```

2.3 安装

树莓派性能有限，不推荐在树莓派系统上运行ROS的GUI工具，所以安装ROS的基本功能包即可

```shell
sudo apt-get update #更新软件源
sudo apt-get install ros-kinetic-desktop-base #ros-kinetic-desktop-full 
sudo rosdep init #安装rosdep工具
rosdep update
```

```shell
source /opt/ros/noetic/setup.bash //可有可无
echo “source /opt/ros/kinetic/setup.bash” >> ~/.bashrc
source ~/.bashrc
```

安装其他功能包

```shell
sudo apt-get install python-rosinstall python-rosinstall-generator python-wstool build-essential
```

