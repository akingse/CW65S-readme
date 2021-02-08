

---

## Ubuntu指令

[引用](https://www.cnblogs.com/flyingjun/p/8794951.html)

[Unix初学教程](http://www.ee.surrey.ac.uk/Teaching/Unix/) 

### 截屏 Shift + Ctrl + PrtSc

![image-20201218222636940](https://i.loli.net/2020/12/18/hg7MFJmRUvZws5k.png)

> - PrtSc – 获取整个屏幕的截图并保存到 Pictures 目录。
> - Shift + PrtSc – 获取屏幕的某个区域截图并保存到 Pictures 目录。
> - Alt + PrtSc –获取当前窗口的截图并保存到 Pictures 目录。
> - Ctrl + PrtSc – 获取整个屏幕的截图并存放到剪贴板。
> - Shift + Ctrl + PrtSc – 获取屏幕的某个区域截图并存放到剪贴板。
> - Ctrl + Alt + PrtSc – 获取当前窗口的 截图并存放到剪贴板。

```
sudo apt-get install flameshot #商店安装
sudo apt-get install shutter
GIMP图片编辑器
```

![image-20201218222744665](https://i.loli.net/2020/12/18/V493vjmDATeFrW6.png)

### ls (list)

```shell
ls -a 隐藏文件
mkdir (make directory)
cd (change directory)
(.) means the current directory 当前目录
(..) means the parent of the current directory 父目录
pwd (print working directory)查看当前路径命令：pwd
~ (your home directory) 家目录
cp (copy)
rm (remove), rmdir (remove directory)
clear (clear screen) Ctrl+L
cat (concatenate)
ls -l (l for long listing!)
chmod (changing a file mode)
ps (process status)
history (show command history list)
```



---

## 常用命令

```shell
cd /home/akingse/下载/wechatfile
sudo cp -r cmake-3.15.3.tar.gz /opt/ #复制
tar -xvf cmake-3.15.3.tar.gz #解压
sudo chmod 777 fielname #修改文件读写权限
sudo mv old new #重命名文件夹 
sudo rm -r name #删除文件夹 
sudo rm name #删除文件 
ls -lha #查看隐藏文件
sudo su #切换到root用户
sudo nautilus #用root权限打开文件浏览器，对所有文件拥有最高的读写权限。
```



#### 文件属性

```shell
ls -l
drwxrwxr-x  9 akingse akingse 4096 1月   5 20:42 catkin_ws
d rwx rwx rwx
d是文件目录
rwx分别为读、写、执行权限，-表示没有权限
第0位确定文件类型，第1-3位确定属主（该文件的所有者）拥有该文件的权限。
第4-6位确定属组（所有者的同组用户）拥有该文件的权限，第7-9位确定其他用户拥有该文件的权限。
chmod：更改文件9个属性
chmod 777 filename #最多权限
```



#### shell命令 /bin/bash

Linux的目录结构为树状结构，最顶级的目录为根目录 /
绝对路径，由根目录 / 写起，例如： /usr/share/doc 这个目录。
 .  代表当前的目录，也可以使用 ./ 来表示；
 ..  代表上一层目录，也可以 ../ 来代表。
如果一个目录或文件名以一个点 . 开始，表示这个目录或文件是一个隐藏目录或文件(如：.bashrc)

akingse@cw65s-ubuntu:~$  ～表示当前用户目录/home/akingse
akingse@cw65s-ubuntu:/$  /表示绝对根目录
cd命令：Change directory

```shell
cd ~ #当前用户根目录 home/akingse
cd .. #回到上一级
cd - #返回到上一次的工作目录

cat 命令用于连接文件并打印到标准输出设备上。
pwd: print work directory 显示/打印当前目录
mkdir：Make Directory(创建目录)
```

---

### Roboware快捷键

> Ctrl+～ 新建集成终端
> Ctrl+shift+～ 新建集成终端新标签
> #gnome终端快捷键
> Ctrl+alt+T 新建 （左手，小拇指 大拇指 食指）
> Ctrl+shift+T 标签内新建
>
> Ctrl + C
> 立刻终止运行的程序
> Ctrl + Z
> 将正在运行的程序送到后台
> Ctrl + D
> 退出当前终端
> Ctrl + L  # clear
> 清空你的终端屏幕
>
> Ctrl + A  /  Ctrl + E
> 移动光标到行首 / 移动光标到行尾
> Ctrl + U  /  Ctrl + K  /  Ctrl + W
> 擦除从当前光标位置到行首的全部内容/从当前光标位置到行尾 / 擦除光标位置前的单词
> Ctrl + Y
> 删除了错误的文本或需要在某处使用已擦除的文本
> Ctrl + P / Ctrl + N
> 查看上一个命令 / 显示下一个命令
> Ctrl + R
> 搜索历史命令
> 桌面程序切换成控制台 Ctrl + Alt + F2 //Ctrl + Alt + F7

---

## Ubuntu系统C盘目录

```
/bin = Binaries (二进制文件)
/dev = Devices (设备)
/etc = Etcetera (等等)
/lib = LIBrary
/proc = Processes
/sbin = Superuser Binaries (超级用户的二进制文件)
/tmp = Temporary (临时)
/usr = Unix Shared Resources
/var = Variable (变量)
```

/bin：
bin是Binary的缩写, 这个目录存放着最经常使用的命令。
/boot：
这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件。
/dev ：
dev是Device(设备)的缩写, 该目录下存放的是Linux的外部设备，在Linux中访问设备的方式和访问文件的方式是相同的。
/etc：
这个目录用来存放所有的系统管理所需要的配置文件和子目录。
/home：
用户的主目录，在Linux中，每个用户都有一个自己的目录，一般该目录名是以用户的账号命名的。
/lib：
这个目录里存放着系统最基本的动态连接共享库，其作用类似于Windows里的DLL文件。几乎所有的应用程序都需要用到这些共享库。
/lost+found：
这个目录一般情况下是空的，当系统非法关机后，这里就存放了一些文件。
/media：
linux系统会自动识别一些设备，例如U盘、光驱等等，当识别后，linux会把识别的设备挂载到这个目录下。
/mnt：
系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在/mnt/上，然后进入该目录就可以查看光驱里的内容了。
/opt：
 这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则就可以放到这个目录下。默认是空的。
/proc：
这个目录是一个虚拟的目录，它是系统内存的映射，我们可以通过直接访问这个目录来获取系统信息。
/root：
该目录为系统管理员，也称作超级权限者的用户主目录。
/sbin：
s就是Super User的意思，这里存放的是系统管理员使用的系统管理程序。
/selinux：
 这个目录是Redhat/CentOS所特有的目录，Selinux是一个安全机制，类似于windows的防火墙，但是这套机制比较复杂，这个目录就是存放selinux相关的文件的。
/srv：
 该目录存放一些服务启动之后需要提取的数据。
/sys：
 这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个文件系统 sysfs 。
/tmp：
这个目录是用来存放一些临时文件的。
/usr：
 这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似于windows下的program files目录。
/var：
这个目录中存放着在不断扩充着的东西，我们习惯将那些经常被修改的目录放在这个目录下。包括各种日志文件。

---

### 使用python编译

进入shiyanlou文件夹

```
cd /home/akingse/shiyanlou
```

用Python3打开文件

```shell
python3 MinutesToHours.py
python3 /home/akingse/shiyanlou/MinutesToHours.py 80
```



### 使用gcc编译

gcc是GNU Compiler Collection，也可以简单认为是编译器，它可以编译很多种编程语言.当你的程序只有一个源文件时，直接就可以用gcc命令编译它。
gcc在执行编译工作的时候，总共需要4步：
.i -> .s -> .o -> exe
对于C：gcc [options] [exefile] [filenames]#将文件file1编译成可执行文件file2
对于c++：g++ [options] [exefile] [filenames]
-o FILE，生成指定的输出文件。用在生成可执行文件时。

```
gcc -o hello hello.c
g++ -o hello hello.cpp
./hello #执行可执行文件
```

gcc -Wall -W test.cpp -o test  #-o file1 [file2]
-Wall 开启GCC最常用的警告，GCC的warning一般格式为file:line-number:message

## 使用cmake编译

### 安装cmake

```shell
cd cmake-3.15.3
sudo ./bootstrap 
sudo make 
sudo make install 
anno #CMake -version 
cmake --version #验证成功
```

### 使用cmake

然后用cmake命令将CMakeLists.txt文件转化为make所需要的makefile文件，最后用make命令编译源码生成可执行程序或共享库
*内部编译*，即直接在工程目录下进行构建，生成的中间文件也在工程目录下，这样显得很乱;

```
cd /home/akingse/shiyanlou/domec/test-cmake
```

新建 main.cpp CMakeLists.txt （学名：组态档）

```
cmake .
make #生成 hello 可执行文件
./hello
```

外部编译：建立一个名为build的目录,在build目录内使用终端命令，生成的所有文件均在build内，不影响main.cpp CMakeLists.txt

```shell
mkdir build # /test-cmake/build
cd build
cmake ..  #..代表当前目录的父目录
make
```



---



