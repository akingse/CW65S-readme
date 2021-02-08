### 修复win(super)+D

- settings->hardware->keyboard->shortcuts->navigation->(hide all normal windows)
- unity tweak tools->launcher->show desktop icon(上方第一个)

### 扩展屏幕管理

```shell
xrandr

eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
HDMI-1 connected 2560x1440+1920+0 (normal left inverted right x axis y axis) 527mm x 296mm

xrandr --output HDMI-1 --left-of eDP-1 --auto
xrandr --output HDMI-1 --auto --output eDP-1 --off 
nice
```

```shell
xrandr --output HDMI-1 --same-as eDP-1 --auto
	打开外接显示器(--auto:最高分辨率)，与笔记本液晶屏幕显示同样内容（克隆）
xrandr --output HDMI-1 --same-as eDP-1 --mode 2560x1440
	打开外接显示器(分辨率为1280x1024)，与笔记本液晶屏幕显示同样内容（克隆）
xrandr --output HDMI-1 --right-of eDP-1 --auto
	打开外接显示器(--auto:最高分辨率)，设置为右侧扩展屏幕
xrandr --output HDMI-1 --off
	关闭外接显示器
xrandr --output HDMI-1 --auto --output eDP-1 --off
	打开外接显示器，同时关闭笔记本液晶屏幕（只用外接显示器工作）
xrandr --output HDMI-1 --off --output eDP-1 --auto
	关闭外接显示器，同时打开笔记本液晶屏幕 （只用笔记本液晶屏） 
```

复杂了，系统设置里有分屏操作；

### ubuntu16.04系统深色模式

[简书](https://www.jianshu.com/p/4bd2d9b1af41)

```shell
sudo apt-get install unity-tweak-tool 
sudo apt-get install gnome-tweak-tool

sudo apt-get remove unity-tweak-tool
sudo apt-get remove gnome-tweak-tool

gnome-tweak-tool
#python bug，可能16.04不兼容吧
---

sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
sudo apt-get install flatabulous-theme

macubuntu
sudo add-apt-repository ppa:noobslab/macbuntu
sudo apt-get update
sudo apt-get install  macbuntu-os-ithemes-lts-v7
sudo apt-get install  macbuntu-os-icons-lts-v7
sudo apt-get install  macbuntu-os-plank-itheme-lts-v7 

再来一遍，nice，成功了
sudo add-apt-repository ppa:noobslab/themes
sudo add-apt-repository ppa:noobslab/icons
sudo apt-get update 
sudo apt-get install arc-flatabulous-theme
sudo apt-get install ultra-flat-icons
“Arc-flatabulous-dark”
```

[quote](https://www.jianshu.com/p/4bd2d9b1af41)

修改颜色个性化设置

```
sudo gedit ~root/.bashrc
```

```
if if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\    [\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

```



### 使用gnome设置

terminal->preferences->profiles -> > edit->colors (取消 use colors from system theme,取消 use transparency from system theme )

![image-20201113105720111](/home/akingse/.config/Typora/typora-user-images/image-20201113105720111.png)



---

## 使用VNC



计算机名

CW65S-ubuntu

密码123456

```
sudo apt-get install xrdp vnc4server xbase-clients
sudo apt-get install dconf-editor
```

[quote](https://blog.csdn.net/lxllinux/article/details/81940396)

![image-20201226093223637](https://i.loli.net/2020/12/26/myCeDOj9YsWwP5b.png)

```
sudo systemctl set-default multi-user.target
sudo systemctl set-default graphical.target
```

