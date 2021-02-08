## 记录Qt安装

当前Ubuntu版本：16.04

qt安装包版本：
qt-opensource-linux-x64-5.14.0.run

```shell
sudo chmod +x qt-opensource-linux-x64-5.14.0.run
./qt-opensource-linux-x64-5.14.0.run
sudo ./qt-opensource-linux-x64-5.14.0.run
一个是将 Qt 默认安装在 home 目录下，后者是将 Qt 安装在根目录／opt 下。可能打开时需要权限；
```

登录邮箱 akingse@qq.com

安装位置 /opt/Qt5.14.0

勾选

> Qt 5.14
> 	Desktop gcc
> 	Sources
> Developer and Disigner Tools
> 	Qt Creator



---

修改default.conf

```
sudo gedit /usr/lib/x86_64-linux-gnu/qt-default/qtchooser/default.conf
```

修改成QT_bin路径与QT路径

```
cd /opt/Qt5.14.0/Tools/QtCreator/bin/

opt/Qt5.14.0/5.14.0/gcc_64/bin
opt/Qt5.14.0/

replace
/usr/lib/x86_64-linux-gnu/qt4/bin
/usr/lib/x86_64-linux-gnu
```

卸载qt

cd /opt/Qt5.14.0

```
sudo ./MaintenanceTool
```



#### 添加环境变量（ ~.bashrc 和 /etc/profile ）

环境变量就是当前环境下的参数或者变量。如果说的专业一点就是指在操作系统中用来指定操作系统的一些参数。如最常见的环境变量 ——  PATH，它的用途就是当用户要求系统运行一个程序而没有告诉它程序所在的完整路径时，系统除了在当前目录下寻找此程序外，还要到PATH变量中指定的路径去寻找。用户可以通过设置PATH变量，来更好的运行进程。

.bashrc 文件主要保存着个人的一些个性化设置，如：命令别名、环境变量等。

```
cd ~
sudo gedit .bashrc
sudo gedit /home/akingse/.bashrc
sudo gedit ~/.bashrc
```

PATH=${PATH}:opt/Qt5.14.0/5.14.0/gcc_64/bin:opt/Qt5.14.0/Tools/QtCreator/bin
#安装gcc才有gcc_64

```
source .bashrc 
```

/etc/profile 文件是系统为每个用户设置的环境信息，当用户第一次登录时，该文件被执行。此文件的改变会涉及到系统的环境，也就是有关Linux环境变量的东西。

```
sudo gedit /etc/profile
export PATH=/usr/local/cuda-8.0/bin:$PATH  
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64:$LD_LIBRARY_PATH
source /etc/profile
```



#### 权限问题，修改文件权限

查看权限 `ls -l`

-rwxr-xr-x 1 root root 134312 12月 10  2019 qtcreator

```
-文件类型
rwx 所有者权限
r-x 组用户权限
r-x 其他用户权限
1 链接数/子目录
root 用户名
root 组名
134312 文件大小
12月 10  2019 修改日期
qtcreator 文件名
#drwxrwxrwx，全部权限，文件名会加绿
```

[引用](https://blog.csdn.net/huxinguang_ios/article/details/81026811)

---

### bug

```
./qtcreator
./qtcreator: symbol lookup error: /opt/geomagic_touch_device_driver/lib/plugins/sqldrivers/libqsqlite.so: undefined symbol: _ZN16QSqlCachedResultC2EPK10QSqlDriver

cd /opt/Qt5.14.0/Tools/QtCreator/bin
sudo ./qtcreator

```



```
sudo cp libfreetype.so* /opt/Qt5.14.0/Tools/QtCreator/lib/Qt/lib -v
```

图标文件位置

查找文件命令 `find -name "*qt*"`

```
gedit ~/.local/share/applications/DigiaQtOpenSource-qtcreator.desktop

gedit /usr/share/applications/
```



```
[Desktop Entry]
Type=Application
Exec=bash -i -c /opt/Qt5.14.0/Tools/QtCreator/bin/qtcreator
Name=Qt_Creator
GenericName=The IDE of choice for Qt development.
Icon=QtProject-qtcreator
Terminal=false
Categories=Development;IDE;Qt;
MimeType=text/x-c++src;text/x-c++hdr;text/x-xsrc;application/x-designer;application/vnd.qt.qmakeprofile;application/vnd.qt.xml.resource;text/x-qml;text/x-qt.qml;text/x-qt.qbs;
```

没有修复成功，只能./打开；