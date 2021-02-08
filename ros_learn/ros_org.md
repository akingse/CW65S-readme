## [ROS官方教程](http://wiki.ros.org/cn/ROS/Tutorials)

### 1.核心ROS教程-初级



```shell
printenv | grep ROS #
```

> ROS_ROOT=/opt/ros/kinetic/share/ros
> ROS_PACKAGE_PATH=/home/akingse/catkin_ws/src:/home/akingse/tutorial_ws/src:/opt/ros/kinetic/share
> ROS_MASTER_URI=http://localhost:11311
> ROS_PYTHON_VERSION=2
> ROS_VERSION=1
> ROSLISP_PACKAGE_DIRECTORIES=/home/akingse/catkin_ws/devel/share/common-lisp:/home/akingse/tutorial_ws/devel/share/common-lisp
> ROS_DISTRO=kinetic
> ROS_ETC_DIR=/opt/ros/kinetic/etc/ros

### source FileName

> source FileName，source命令作用：在当前bash环境下读取并执行FileName中的命令。
>
> 该命令通常用命令“.”来替代。
> 1.当shell脚本具有可执行权限时，用sh filename与./filename执行脚本是没有区别得。./filename是因为当前目录没有在PATH中，所有"."是用来表示当前目录的。
> 2.sh filename 重新建立一个子shell，在子shell中执行脚本里面的语句，该子shell继承父shell的环境变量，但子shell新建的、改变的变量不会被带回父shell，除非使用export。
> 3.source filename：这个命令其实只是简单地读取脚本里面的语句依次在当前shell里面执行，没有建立新的子shell。那么脚本里面所有新建、改变变量的语句都会保存在当前shell里面。
> Linux中shell脚本的执行通常有4种方式，分别为工作目录执行，绝对路径执行，sh执行，shell环境执行。
> ./的意思是说在当前的工作目录下执行hello.sh。./代表执行当前路径下的某个命令
> 绝对路径中执行，指的是直接从根目录/到脚本目录的绝对路径
> sh执行，指的是用脚本对应的sh或bash来接着脚本执行
> shell环境执行，指的是在当前的shell环境中执行，可以使用 . 接脚本 或 source 接脚本

### shell脚本

```shell
echo $SHELL
cat /etc/shells
```

> shell是linux的一个外壳，它包在linux内核的外面，为用户和内核之间的交互提供了一个接口。
> 简单的来说，当命令或者程序不在命令行执行，而是通过一个程序文件来执行，这个程序就称为为shell脚本
> bash 是一个为GNU计划编写的Unix shell。它的名字是一系列缩写：Bourne-Again SHell — 这是关于Bourne shell（sh）的一个双关语（Bourne again / born again）,是许多Linux发行版的默认Shell 。

***\*外部构建\****，中间文件和可执行文件都将存放在build目录中。

***\*内部构建\****，cmake生成的所有中间文件和可执行文件都会存放在项目目录中

```shell
$ mkdir -p ~/catkin_ws/src #创建一个[catkin工作空间](http://wiki.ros.org/catkin/workspaces)
$ cd ~/catkin_ws/src #在'src'目录中没有任何软件包，只有一个CMakeLists.txt链接文件
$ cd ~/catkin_ws/build
$ cmake ..  $ make #..父目录；.当前目录
```

之前比较菜，非要加个指令提示符号$$，生怕自己不知道这是句shell语句；

### catkin_make

> catkin_make是cmake的高级封装，路径是定义好的，用户只需要按照catkin_make的文件管理规则使用即可。
> catkin_make 与cmake
> cmake编译是这样的流程, cmake指令依据你的CMakeLists.txt 文件,生成makefiles文件,make再依据此makefiles文件编译链接生成可执行文件. catkin_make是将cmake与make的编译方式做了一个封装的指令工具, 规范了工作路径与生成文件路径。
> CMake编译原理 （不使用 IDE 直接用命令行编译成可执行文件）
> CMake是一种跨平台编译工具。CMake主要是编写CMakeLists.txt文件，然后用cmake命令将CMakeLists.txt文件转化为make所需要的makefile文件，最后用make命令编译源码生成可执行程序或共享库（so(shared object)）。因此CMake的编译基本就两个步骤：cmake和make
> CMake是一个跨平台的安装（编译）工具，可以用简单的语句来描述所有平台的安装(编译过程)。能够输出各种各样的makefile或者project文件，能测试编译器所支持的C++特性,类似UNIX下的automake。只是 CMake 的组态档取名为 CMakeLists.txt。

```shell
#catkin_make 编译
$ gcc -o/g++ -o exe x.c #编译c/c++文件，./ 执行；
$ python3 name.py #python无需编译，直接执行；
$ cd build $ cmake .. $ make #cmake外部编译,中间文件和exe都放在build目录中。
$ catkin_make #编译整个工作空间所有package；
#catkin是将camke和make指令做了一个封装从而完成整个编译过程的工具。
```

### catkin编译系统  

> [quote](https://blog.csdn.net/weixin_41070687/article/details/82079308)
> package.xml（功能包配置文件）
> 定义了package的属性（包的自我描述），如包名、版本号、作者、依赖等
> CMakeList.txt（构建配置文件）
> 规定了catkin的编译规则，是构建package所需的CMake文件，具体的有：调用catkin的函数/宏；解析package.xml；找到其他依赖的catkin软件包；将本软件包添加到环境变量等等
> catkin编译的工作流程
> 首先在工作空间的src目录下递归的查找每一个ros的package。因为每一个package中都有package.xml和CMakeList.txt文件，所以catkin编译系统依据CMakeList.txt文件，生成makefile文件，放在工作空间的build文件夹中。然后make刚刚生成的makefiles等文件，编译链接生成可执行文件，放在工作空间下的devel文件夹。
> 简而言之，catkin就是将camke和make指令做了一个封装从而完成整个编译过程的工具。

### make

> make是一条计算机指令，是在安装有GNU Make的计算机上的可执行指令。该指令是读入一个名为makefile 的文件，然后执行这个文件中指定的指令，用来编译和链接程序。
> make是一个命令工具，是一个解释makefile中指令的命令工具，一般来说，大多数的IDE都有这个命令。常见几种 Make 工具，例如 GNU Make ，QT 的 qmake ，微软的 MS nmake等等。这些 Make 工具遵循着不同的规范和标准，所执行的 Makefile 格式也千差万别。
> makefile定义了一系列的规则来指定编译顺序，甚至于进行更复杂的功能操作，makefile就像一个Shell脚本一样，其中也可以执行操作系统的命令。makefile带来的好处就是“自动化编译”，只需要一个make命令，整个工程完全自动编译，极大的提高了软件开发的效率。
> CMake就是针对跨平台编译问题所设计的工具：它首先允许开发者编写一种平台无关的 CMakeList.txt 文件来定制整个编译流程，然后再根据目标用户的平台进一步生成所需的本地化 Makefile 和工程文件。
> [quote](https://blog.csdn.net/lisfaf/article/details/90411862)
> make工具可以看成是一个智能的批处理工具，通过调用makefile文件中用户指定的命令来进行编译和链接的。makefile命令中就包含了调用gcc等编译器去编译某个源文件的命令。
> 使用CMake这个工具，cmake就可以更加简单的生成makefile文件给make用。当然cmake还有其他功能，可以跨平台生成对应平台能用的makefile。cmake根据一个叫CMakeLists.txt文件（学名：组态档）去生成makefile。最后CMakeLists.txt文件需要自定义。

### CMakeLists.txt

并保存在与main.cpp源文件同个目录下

```
cmake_minimum_required (VERSION 2.8) # CMake 最低版本号要求
project (mathPowerDemo) # 项目信息，该命令表示项目的名称是 mathPowerDemo
add_executable(mathPowerDemo main.cpp) # 指定生成目标，将名为 main.cpp的源文件编译成一个名称为 	mathPowerDemo 的可执行文件。
```

### pakege.xml

> Packages: 软件包，是ROS应用程序代码的组织单元，每个软件包都可以包含程序库、可执行文件、脚本或者其它手动创建的东西。 
> package.xml: 软件包标签
> package.xml也是一个catkin的package必备文件， 它是这个软件包的描述文件。pacakge.xml 包含了package的名称、版本号、内容描述、维护人员、软件许可、编译构建工具、 编译依赖、 运行依赖等信息。
>   实际上 rospack find 、 rosdep 等命令之所以能快速定位和分析出package的依赖项信息， 就是直接读取了每一个pacakge中的 package.xml 文件。 它为用户提供了快速了解一个pacakge的渠道。
>
> Packages: 软件包，是ROS应用程序代码的组织单元，每个软件包都可以包含程序库、可执行文件、脚本或者其它手动创建的东西。是对于'软件包'相关信息的描述,用于定义软件包相关元信息之间的依赖关系，这些信息包括版本、维护者和许可协议等。

```
   <description>The beginner_tutorials package</description> #更新描述标签
   <maintainer email="you@yourdomain.tld">Your Name</maintainer> #维护者标签
   <license>BSD</license> #选择一种许可协议并将它填写到这里。ROS核心组件使用了BSD协议
   <buildtool_depend>catkin</buildtool_depend> #依赖项标签，用来描述程序包的各种依赖项，这些依赖项分为build_depend、buildtool_depend、run_depend、test_depend。
```

基本概念

> [nodes](http://wiki.ros.org/Nodes):节点,一个节点即为一个***\*可执行文件\****，它可以通过ROS与其它节点进行通信。
>
> [messages](http://wiki.ros.org/Messages):消息，消息是一种ROS***\*数据类型\****（.msg），用于订阅或发布到一个话题。
>
> [topics](http://wiki.ros.org/Topics):话题,节点可以发布消息到话题，也可以订阅话题以接收消息。
>
> [Master](http://wiki.ros.org/Master):节点管理器，ROS名称服务 (比如帮助节点找到彼此)。
>
> [rosout](http://wiki.ros.org/rosout): ROS中相当于stdout/stderr。rosout是ROS中控制台日志报告机制的名称
>
> [roscore](http://wiki.ros.org/roscore): 主机+ rosout + param参数服务器。

***\*rosnode\****

```
$ rosnode info /turtlesim #查看节点信息
$ rosnode list  #查看正在运行的节点
/rosout  #这个节点用于收集和记录节点调试输出信息，它总是在运行的。
/turtlesim #小海龟仿真
```

***\*rosrun #\****启动一个Node：

```
语法 rosrun [package_name] [node_name] #rosrun package-name executable-name
rosrun 允许你使用包名直接运行一个包内的节点(而不需要知道这个包的路径)。
$ rosrun turtlesim turtlesim_node  #位置 /opt/ros/kinetic/lib/turtlesim
$ rosrun turtlesim turtlesim_node __name:=my_turtlesim #重命名节点，双开小乌龟
$ rosnode ping my_turtle #ping 命令通过ICMP（Internet控制消息协议）工作；ping可以用来测试本机与目标主机是否联通、联通速度如何、稳定性如何。
```

小乌龟

```
$ roscore
$ rosrun turtlesim turtlesim_node
$ rosrun turtlesim turtle_teleop_key
```

***\*rostopic\****命令工具能让你获取有关ROS话题的信息。

```
$ rostopic -h  #Commands:
$ rostopic echo /turtle1/cmd_vel  #查看turtle_teleop_key节点在/turtle1/cmd_vel话题上发布的数据。
rostopic list能够列出所有当前订阅和发布的话题。
$ rostopic list -h
$ rostopic list -v #显示出有关所发布和订阅的话题及其类型的详细信息
# Published topics: 发布者； Subscribed topics: 订阅者；
```

***\*m\*******\*essages\*******\*消息\****

话题之间的通信是通过在节点之间发送ROS消息实现的。对于发布器(turtle_teleop_key)和订阅器(turtulesim_node)之间的通信，发布器和订阅器之间必须发送和接收相同类型的消息。这意味着话题的类型是由发布在它上面的消息类型决定的。

```
$ rostopic type /turtle1/cmd_vel  #查看所发布话题的消息类型：geometry_msgs/Twist 几何/转动
$ rosmsg show geometry_msgs/Twist  #rosmsg命令来查看消息的详细情况
使用 rostopic pub，可以把数据发布到当前某个正在广播的话题上。
语法 rostopic pub [topic] [msg_type] [args]
$ rostopic pub -1 /turtle1/cmd_vel geometry_msgs/Twist -- '[10.0, 0.0, 0.0]' '[0.0, 0.0, 6.28]' 
#发布消息给话题；模式1，发布后马上退出；话题名称；消息类型  持续3秒
#Vector3 linear，半径； Vector3 angular，角度。以2.0大小的线速度和1.8大小的角速度开始移动
rostopic pub -r命令来发布一个稳定的命令流
$ rostopic pub -r 1 /turtle1/cmd_vel geometry_msgs/Twist -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]'
rqt_graph #迅速获取
```

***\*7.\*******\*ROS服务和参数\**** ([rosservice](http://wiki.ros.org/rosservice) , [rosparam](http://wiki.ros.org/rosparam))（同步通信）

使用客户端-服务器模型，客户端发送请求数据，服务器完成处理后返回应答数据。

使用与编程语言无关的.srv文件定义请求和应答数据结构，编译过程中生成对应代码文件。

```
服务（services）是节点之间通讯的另一种方式。服务允许节点发送请求（request） 并获得一个响应（response）
$ rosservice -h  #帮助命令
$ rosservice list  #list 命令显示turtlesim节点提供了9个服务
rosservice type 查看服务的类型
rosservice call 调用服务，使用方法:rosservice call [service] [args]
$ rosservice call clear #清除turtlesim_node的背景上的轨迹
$ rosservice type spawn| rossrv show #查看（spawn）服务的信息，显示参数
$ rosservice call spawn 2 2 0.2 "" # rosservice call spawn 4 4 0.2 "turtle3"
```

```
rosparam使得我们能够存储并操作ROS 参数服务器（Parameter Server）上的数据。
$ rosparam -h
rosparam set [param_name] 
$ rosparam set background_r 150  #修改背景颜色的红色通道
rosparam get [param_name] 
$ rosparam get background_r #获取背景红色通道r值 
$ rosparam get /
$ rosservice call /spawn "x: 5.0 #新生成一只海龟
$ rosservice call clear  #调用清除服务使得修改后的参数生效
rosparam dump [file_name] 
$ rosparam dump params.yaml #将所有参数写入params.yaml文件，home目录
rosparam load [file_name] [namespace]
```

***\*8.\*******\*rqt_console 和 roslaunch\****

```
rqt_console属于ROS日志框架(logging framework)的一部分，用来显示节点的输出信息。
rqt_logger_level允许我们修改节点运行时输出信息的日志等级（logger levels）
$ rosrun rqt_console rqt_console
$ rosrun rqt_logger_level rqt_logger_level
新终端中启动turtlesim：$ rosrun turtlesim turtlesim_node
让turtle动起来并观察rqt_console中的输出
$ rostopic pub /turtle1/cmd_vel geometry_msgs/Twist -r 1 -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 0.0]'

roslaunch可以用来启动定义在launch文件中的多个节点。roslaunch使用的是xml语言。
roslaunch [package] [filename.launch]
通过roslaunch命令来启动launch文件：
$ roslaunch beginner_tutorials turtlemimic.launch
```

总结

```shell
rospack = ros+pack(age) : provides information related to ROS packages
rosstack = ros+stack : provides information related to ROS stacks
roscd = ros+cd : changes directory to a ROS package or stack
rosls = ros+ls : lists files in a ROS package
roscp = ros+cp : copies files from/to a ROS package
rosmsg = ros+msg : provides information related to ROS message definitions
rossrv = ros+srv : provides information related to ROS service definitions
rosmake = ros+make : makes (compiles) a ROS package
```

***\*17.\*******\*录制与回放数据\****



录制所有发布的话题

```
rostopic list -v  #检查看当前系统中发布的所有话题
rosrun turtlesim turtlesim_node 
rosrun turtlesim turtle_teleop_key
rosbag record -a
建立一个用于录制的临时目录 /bagfiles，然后在该目录下运行rosbag record命令，并附加-a选项，该选项表示将当前发布的所有话题数据都录制保存到一个bag文件中。
rosbag info <your bagfile> #使用rosbag info检查看它的内容
rosbag play <your bagfile> #使用rosbag play命令回放出来，bagfiles目录下
rosbag play -r 2 <your bagfile> #参数选项是-r选项，它允许你通过设定一个参数来改变消息发布速率。
录制数据子集
rosbag record命令支持只录制某些特别指定的话题到单个bag文件中，这样就允许用户只录制他们感兴趣的话题。
在bag文件所在目录下执行以下命令：
rosbag record -O subset /turtle1/command_velocity /turtle1/pose
```



---

## Roboware使用

1新建ROS包
![image-20201210165813372](https://i.loli.net/2020/12/10/d5eCDi87vB4ZmjW.png)

- CMakeLists.txt #配置文件

- package.xml #清单文件

2新建源文件，加入到新的可执行文件中
<img src="https://i.loli.net/2020/12/10/JiXE2GpAgzWFaQP.png" alt="image-20201210165818596"  />

3编辑依赖的ROS包列表
![image-20201210165826623](/home/akingse/.config/Typora/typora-user-images/image-20201210165826623.png)

sensor_msgs joy geometry_msgs roscpp rospy std_msgs message_generation



ROS-构建：（catkin_make）

集成终端（/bin/bash）运行：

```
$ roscore
$ rosrun beginner_tutorials talker
$ rosrun beginner_tutorials listener
```

 

***\*调试\****

> 资源管理器->选择“Debug”模式
> 调试>选择C++
> 资源管理器->ROS 节点 
> 调试界面->配置参数 param1 param2 param 回车
> 启动调试





















