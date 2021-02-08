# Ubuntu使用教程
​    安装软件：apt-get install 软件1 软件2
​    卸载软件：apt-get remove 软件1 软件2
​    卸载并清除配置：apt-get remove --purge 软件名
​    更新软件信息数据库 apt-get update
​    进行系统升级 apt-get upgrade

​    安装deb软件包 dpkg -i xxx.deb
​    删除deb软件包 dpkg -r xxx.deb
​    连同配置文件一起删除 dpkg -r --purge xxx.deb

```
sudo dpkg -i sogoupinyin_2.3.1.0112_amd64.deb
sudo apt-get install sogoupinyin_2.3.1.0112_amd64.deb
```



## 使用wine平台
[下载地址](https://github.com/wszqkzqk/deepin-wine-ubuntu)  

```
git clone https://github.com/wszqkzqk/deepin-wine-ubuntu.git
```

文件名：deepin-wine-ubuntu-master（第一次装的master版）
解压后切换到解压文件目录

```
./install.sh #安装
```

下载对应dep安装包
使用dpkg -i安装容器(.deb) #目录下，tab自动补齐

```
sudo dpkg -i /home/akingse/下载/deepin.com.wechat_2.6.2.31deepin0_i386.deb
sudo dpkg -i /home/akingse/下载/netease-cloud-music_1.1.0_amd64_deepin.deb
```

启动网易云音乐

```
sudo netease-cloud-music
```

wechat

临时文件存储位置

```
/home/akingse/文档/WeChat Files/weixin-SWQS/FileStorage/File/2020
卸载
sudo apt-get autoremove deepin.com.wechat #tab查看
```

修复微信bug
/opt/deepinwine
显示隐藏文件 ls -lha

```
cp deepin.com.wechat.desktop /home/akingse
sudo mv deepin.com.wechat.desktop /home/akingse
sudo mv deepin.com.qq.office.desktop /home/akingse
```

Deepin-WeChat

```
sudo cp deepin.com.wechat.desktop /usr/share/applications
sudo cp deepin.com.qq.office.desktop /usr/share/applications

sudo cp deepin.com.wechat.desktop /opt/deepinwine/apps/Deepin-TIM
sudo mv 
"/opt/deepinwine/apps/Deepin-TIM/run.sh" -u %u
"/opt/deepinwine/apps/Deepin-WeChat/run.sh" -u %u
```

微信无法发送图片可以尝试一下这个方法
终端执行：

```
sudo apt install libjpeg62:i386
```



## 安装pycharm.tar.gz 
如pycharm-community-2019.2.tar.gz
1 进入文件目录

```
cd /home/akingse/
```

解压（或者右键压缩->提取到此处）

```
tar xvzf xxx.tar.gz 
```

2 进解压目录的bin文件夹 

```
cd /home/akingse/下载/pycharm-community-2019.2/bin
```

3 执行安装 

```
./pycharm.sh
```

启动pycharm

```
cd /home/akingse/下载/pycharm-community-2019.2/bin
./pycharm.sh
或者
sh ~/home/akingse/下载/pycharm-community-2019.2/bin/pycharm.sh & 
```



### 安装pycharm专业版破解

(1) 复制解压后的安装包至/opt/目录下 

```
sudo cp -r pycharm-2019.2.3 /opt/
```

(2) 将破解文件jetbrains-agent.jar复制到/opt/下的pycharm包中的bin文件夹里 

```
sudo cp -r jetbrains-agent.jar /pycharm-2019.2.3/bin/
```

(3) 配置破解 
将-javaagent:/opt/pycharm-2019.2.3/bin/jetbrains-agent.jar追加到/opt/pycharm-2019.2.3/bin/下的pycharm.vmoptions和pycharm64.vmoptions两个文件中的最后一行
-javaagent:/home/akingse/jetbrains/clion-2019.2.3/bin/jetbrains-agent.jar
(4) 安装程序 
将终端切换至/opt/pycharm-2019.2.3/bin/

```
sudo ./pycharm.sh
```

(5) 激活 
到激活步骤时，将jetbrains-agent-latest文件夹中的jetbrains-agent中的ACTIVATION_CODE.txt里面的激活码复制到激活框中

---

## 安装URsim 

（官方称仅支持Ubuntu14.04）
[下载地址](https://www.universal-robots.com/download/?option=16451#section16447)

URSim_Linux-3.11.0.82155.tar.gz #文件名 
CLion-193.4099.17.tar.gz

```
cd /home/akingse/下载  #进入目录
tar xvzf [FILE NAME] #解压文件指令
tar xvzf URSim_Linux-3.11.0.82155.tar.gz（或者右键解压）
cd ursim-3.11.0.82155 #进入解压后的目录
```

#./install.sh  #安装 (fail) ./start-ursim.sh

## 安装 Roboware studio

安装pip3 #通用的Python包管理工具。提供了对Python包的查找、下载、安装、卸载的功能。
区分python3版本 

```
sudo apt-get install pip3或者sudo apt-get install python3-pip
pip3 -V
sudo pip3 install --upgrade pip
```

[官网手册](https://github.com/TonyRobotics/RoboWare/tree/master/Studio)

python插件

```
sudo python3 -m pip install pylint
sudo apt-get install clang-format-3.8

sudo dpkg -i roboware-studio_1.1.0-1514335284_amd64.deb
最新 
sudo dpkg -i roboware-studio_1.2.0-1524709819_amd64.deb
```

弹出‘最终用户协议’，esc退出，enter同意
稍等，安装成功Dash可见
（科普：左侧状态栏，Launche。Ubuntu搜索中心，Dash。HUD，即 Head Up Display，配合LibreOffice）


---

## 安装ros

```
sudo mkdir -p catkin_ws/src
cd catkin_ws/src
anno# cd /home/akingse/catkin_ws
sudo git clone -b kinetic-devel https://github.com/ros-industrial/universal_robot.git
cd ..
rosdep update
rosdep install --from-paths src --ignore-src --rosdistro kinetic
catkin_make
source /home/akingse/catkin_ws/devel/setup.bash
source /opt/ros/kinetic/setup.bash
```



---

### U盘只读

1.插入U盘并用df -h命令查看文件系统信息:

```
df -h
```

文件系统名称                            挂载点
/dev/sdc1        16G  3.8G   12G   26% /media/akingse/AKING
2.卸载U盘 ，卸载之后不能拔掉U盘

```
sudo umount /media/akingse/AKING
```

3.修复U盘文件系统故障

```
sudo dosfsck -v -a /dev/sdc1
```

4.重新挂载U盘即可解决。(拔了再插)

### 加载机械硬盘

```
sudo ntfsfix /dev/sdb1  #HGST500机械盘
```

加载移动固态，安装格式支持

```
sudo apt-get install exfat-fuse exfat-utils
```

扩展屏幕

```
xrandr --output HDMI-1 --left-of eDP-1 --auto
xrandr
Screen 0:eDP-1 connected primary
HDMI-1 connected
auto #自动分辨率
```



### 修改IP地址

```
ifconfig #查看网卡配置信息
sudo  gedit /etc/network/interfaces
```

> Link encap:本地环回 
> inet 地址:127.0.0.1  掩码:255.0.0.0
> address 172.16.67.10
> netmask 255.255.255.0
> getway 172.16.67.1
> dns-nameserver 172.16.67.1

ping可以查看是否能连接到某个IP地址。

**ping 127.0.0.2**

---

## 修改python版本

```
python -v
python2
python --version
```

Python 2.7.12

```
python3
python3 --version
```

Python 3.5.2

Ctrl+D 停止python
Ctrl+C KeyboardInterrupt

```
cd /usr/bin
ls -l | grep python #显示所有名字中包含python的文件
```

修改

```
sudo rm -rf python

```

python3

```
sudo ln -s /usr/bin/python3  /usr/bin/python
```

python2

```
sudo ln -s /usr/bin/python2  /usr/bin/python
```

---

```
#简简单单
echo alias python=python2 >> ~/.bashrc
source ~/.bashrc

#暴力操作
sudo rm -rf /usr/bin/python
sudo ln -s /usr/bin/python2.7 /usr/bin/python
```



---

### Tab键自动补全

```
sudo gedit /etc/bash.bashrc #打开~./bashrc

```

删除#号
enable bash completion in interactiveshells  之后

```
source /etc/bash.bashrc
```

安装 autojump 自动跳转插件

```
sudo apt-get install autojump
```

配置教程：cat /usr/share/doc/autojump/README.Debian

```
sudo gedit .bashrc
```

在最后一行加入

```
. /usr/share/autojump/autojump.sh
source ~/.bashrc
autojump --version
```

语法高亮插件



---

### 自动打卡

chrome-chromedrive
网页自动化工具
安装驱动
ChromeDriver的版本号要与本机安装的Chrome浏览器的版本相同 83.0.4103.106

unzip chromedriver_linux64.zip

```
chmod +x chromedriver
sudo mv -f chromedriver /usr/local/share/chromedriver
sudo ln -s /usr/local/share/chromedriver /usr/local/bin/chromedriver
sudo ln -s /usr/local/share/chromedriver /usr/bin/chromedriver
```

安装Python依赖

```
pip3 install selenium
pip3 install pyvirtualdisplay
```

pip._vendor.urllib3.exceptions.ReadTimeoutError: 
HTTPSConnectionPool(host='files.pythonhosted.org', port=443): Read timed out.

### Linux设置鼠标滑轮速度

```
sudo apt install imwheel

sudo gedit ~/.imwheelrc

#killall imwheel
imwheel

gnome-session-properties#开机自启
```

