## 串口

> 串行接口简称串口，也称[串行通信](https://baike.baidu.com/item/串行通信)接口或[串行通讯接口](https://baike.baidu.com/item/串行通讯接口/4159201)（通常指[COM接口](https://baike.baidu.com/item/COM接口)），是采用串行通信方式的扩展接口。串行[接口](https://baike.baidu.com/item/接口) （Serial Interface）是指数据一位一位地顺序传送。其特点是[通信线路](https://baike.baidu.com/item/通信线路/1527630)简单，只要一对传输线就可以实现双向通信（可以直接利用电话线作为传输线），从而大大降低了成本，特别适用于远距离通信，但传送速度较慢。
>
> 同步串行接口（英文：SynchronousSerialInterface，SSI）是一种常用的工业用[通信接口](https://baike.baidu.com/item/通信接口)。。
>
> 异步串行是指UART（Universal Asynchronous Receiver/Transmitter），通用异步接收/发送。

 

RS-232，也称标准[串口](https://baike.baidu.com/item/串口)，最常用的一种[串行通讯接口](https://baike.baidu.com/item/串行通讯接口)。现在使用简化为9芯D型插座（DB9）

> RS-485是从RS-422基础上发展而来的，所以RS-485许多电气规定与RS-422相仿。RS-485与RS-422的不同还在于其共模输出电压是不同的，RS-485是-7V至+12V之间，而RS-422在-7V至+7V之间

![image-20201214110622889](https://i.loli.net/2020/12/14/H9JiY7uZygO2cUA.png)

UART口、COM口、USB口是指的物理接口形式(硬件)。而TTL、RS-232、RS-485是指的电平标准(电信号)。
0
UART接口：通用异步收发器（Universal Asynchronous Receiver/Transmitter)，UART是串口收发的逻辑电路，这部分可以独立成芯片，也可以作为模块嵌入到其他芯片里，单片机、SOC、PC里都会有UART模块。
COM口：特指台式计算机或一些电子设备上的D-SUB外形(一种连接器结构，VGA接口的连接器也是D-SUB)的串行通信口，应用了串口通信时序和RS232的逻辑电平。
USB口：通用串行总线，和串口完全是两个概念。虽然也是串行方式通信，但由于USB的通信时序和信号电平都和串口完全不同，因此和串口没有任何关系。USB是高速的通信接口，用于PC连接各种外设，U盘、键鼠、移动硬盘、当然也包括“USB转串口”的模块。（USB转串口模块，就是USB接口的UART模块）

UART包含TTL电平的串口和RS232电平的串口。 TTL电平是3.3V的，而RS232是负逻辑电平，它定义+5~+12V为低电平，而-12~-5V为高电平
TTL：TTL指双极型三极管逻辑电路。TTL电平：全双工（逻辑1: 2.4V--5V   逻辑0: 0V--0.5V）
RS-232电平：全双工（逻辑1：-15V--5V  逻辑0：+3V--+15V）
RS-485：半双工、（逻辑1：+2V--+6V  逻辑0： -6V---2V）这里的电平指AB 两线间的电压差。

COM口即串行通讯端口，简称串口
一般我们见到的是两种物理标准。D型9针插头，和 4针杜邦头两种。
UART接口有4个pin（VCC, GND, RX, TX）, 用的TTL电平,  低电平为0(0V)，高电平为1（3.3V或以上）。
D型9针串口，协议有两种：RS-232和RS-485

> RS-232C接口定义(DB9)
> 引脚 定义 符号
> 1 载波检测 DCD（Data Carrier Detect）
> 2 接收数据 RXD（Received Data）
> 3 发送数据 TXD（Transmit Data）
> 4 数据终端准备好 DTR（Data Terminal Ready）
> 5 信号地 SG（Signal Ground）
> 6 数据准备好 DSR（Data Set Ready）
> 7 请求发送 RTS（Request To Send）
> 8 清除发送 CTS（Clear To Send）
> 9 振铃提示 RI（Ring Indicator）

---

## 使用笔记本摄像头

安装驱动
```
$ cd src
$ git clone  https://github.com/bosch-ros-pkg/usb_cam.git usb_cam
$ catkin_make
```
https://blog.csdn.net/qq_21950671/article/details/98595386
1 使用软件库里的uvc-camera功能包
1.1 检查摄像头
lsusb
1.2 安装uvc camera功能包
sudo apt-get install ros-indigo-uvc-camera
1.3 安装image相关功能包
sudo apt-get install ros-kinetic-image-* #view
sudo apt-get install ros-kinetic-rqt-image-view
1.4 运行uvc_camera节点
rosrun uvc_camera uvc_camera_node
1.5 查看图像信息
（1）使用image_view节点查看图像
rosrun image_view image_view image:=/image_raw
#附加选项“image:=/image_raw”是把话题列表中的话题以图像形式查看的选项。
（2）用rqt_image_view节点检查
rqt_image_view image:=/image_raw
（3）使用rviz查看
rviz

2 使用usb_cam软件包
2.1 安装usb_cam软件包

sudo apt-get install ros-kinetic-usb-cam
2.2 启用launch文件

roslaunch usb_cam usb_cam-test.launch



---

## Arduino语法手册（基础版）

[Arduino语法详解_含示例详解](https://www.cnblogs.com/xczr/p/7832015.html)

https://www.cnblogs.com/xczr/p/7832015.html

 

基础 C 语言 关键字

```
if if...else for switch case while do... while break continue return goto


```

语法符号

```
; --语句结束 {} -// --行注释 /* */ --段注释 #define --宏定义 #include --库文件定义


```

 

数据类型

> void boolean - 布尔类型 
>
> char - 字符类型 unsigned char - 无符号字符类型 
>
> byte - 字节类型 
>
> int - 整数类型 unsigned int - 无符号整数类型
>
> word - 长字类型 
>
> long - 长整数类型 unsigned long - 无符号长整数类型 
>
> float - 浮点类型 double - 双精度浮点类型 
>
> string - 字符数组型 String array - 数组类型
>

 

数据类型转换

char() byte() int() word() long() float()

结构

setup() loop()

常量

HIGH/LOW INPUT/OUTPUT true/false

数字 IO

pinMode() digitalWrite() digitalRead()

模拟 IO

analogReference() analogRead() analogWrite()

扩展 IO

tone() noTone() shiftOut() shiftIn() pulseIn()

时间函数

millis() micros() delay() delayMicroseconds()

数学函数

min() max() abs() constrain() map() pow() sqrt()

---

## ROS串口编程学习笔记

https://blog.csdn.net/u014695839/article/details/81209082

 

Ubuntu下的***\*串口助手cutecom\****

1.安装cutecom并打开：

```
sudo apt-get install cutecom
sudo cutecom
```

运行roscore，运行节点看是否能打开串口。如果提示Unable to open port，是由于权限不够引起的，进行如下操作
创建文件:（若使用的是ttyACM将ttyusb替换即可）

Couldn't find executable named serial_port below 

chmod +x serial_port 赋予权限

连接之后，赋予USB口权限

sudo chmod 777 /dev/ttyUSB0

> Software database is broken
>
> It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
>

解决依赖项问题

sudo apt-get install -f

是修复依赖关系(depends)的命令,就是假如你的系统上有某个package不满足依赖条件,这个命令就会自动修复,安装那个package依赖的package。

```
sudo chmod 777 /dev/ttyUSB0

rosrun rosserial_python serial_node.py /dev/ttyUSB0

rostopic pub -1 /servo std_msgs/UInt16 <POS>

rostopic pub servo std_msgs/UInt16  <angle>
```

 

stty -F /dev/ttyUSB0 -a

sudo stty -F /dev/ttyUSB0 ispeed 115200 ospeed 115200 cs8

 

修改usb的波特率： stty -F /dev/ttyUSB0 115200

 

自定义接线

舵机的红线接5V，黑线接地，数据线接9

控制板(ZL-KPZAR)D9 -底板(ZL-KPZ)***\*SD1\****

//不要乱插线，目测usb供电烧坏了。

***\*注意引脚映射有错误\****

![image-20201214142928924](https://i.loli.net/2020/12/14/ZbWz9HXTokhsuIi.png)

实测

13--led

4-beep

6-DJ3

7-DJ4

8-DJ5

---

***\*创客智造\****

学习教程

https://www.ncnynl.com/category/ros-arduino/

专注于开源硬件和软件的学习和应用.Arduino，Raspberry Pi，树莓派，ROS机器人系统， Turtlebot，UAV无人机 