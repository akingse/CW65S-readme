## 机器人操作系统(ROS)浅析——肖军浩（home版）

**查询三连** rosnode list; rosnode info /*; rostopic list; rostopic info /*; rosmsg info * （仅活动话题才可查询）

```shell
#node
rosnode list
rosnode info /*
rostopic list
#topic
rostopic info /*
rostopic echo /*
rosmsg info * 
```

命名区分 package node exec rosrun

```
CMakeLists->project(package_name)
src/*.cpp->ros::init(argc,argv,"node_name") //rqt_graph显示此节点名
CMakeLists->add_executable(exec_name src/*.cpp) //节点名最好与可执行文件名一致
terminal->rosrun package exec_name
```

节点(node)

> ROS程序的运行实例(running instance)被称为节点(node)
> rosrun package-name executable-name 软件包 可执行文件
> rosrun是一个 shell 脚本,能够理解 ROS 的文件组织结构,知道到哪里能找到与给定包名称对应的可执行文件。
> /opt/ros/kinetic/lib/turtlesim/turtlesim_node 不用rosrun直接执行（节点，可执行文件）
> /home/akingse/catkin_ws/devel/lib/beginner_tutorials/test_cpp
> 笔记:
> rosout 节点是一个特殊的节点。/rosout前面的反斜杠“/”表明该节点名称属于全局命名空间。
> 节点名并不一定与对应可执行文件名称相同。/turtlesim；turtlesim_node
> rosrun设置节点的名称,语法如下:rosrun package-name executable-name __name:=node-name

2.7 话题和消息topic-msg
ROS master负责确保发布节点和订阅节点能找到对方;而且消息是直接地从发布节点传递到订阅节点,中间并不经过节点管理器转交。

> 理解话题和消息， topic-msg
> 话题topic是自定义的名字，如 "chatter"
> ros::Publisher pub = n.advertise<std_msgs::String>("chatter", 1000); pub.publish(msg);
> ros::Subscriber sub = n.subscribe("chatter", 1000, chatterCallback); void chatterCallback(const std_msgs::String &msg){}
> 消息msg是一种可以自定义名字和内容的文件类型（一般使用系统内置的消息类型就够了），如 std_msgs/String
> 加载头文件 创建对象，#include <std_msgs/String.h> std_msgs::String msg;
> 区分话题名和消息名
> /turtle1/cmd_vel //话题名  geometry_msgs/Twist //消息名
> 1消息功能包通常以_msgs结尾，复合域Twist首字母一般大写，有多个成员Vecotr3，顶层域xyz
> 2消息类型的命名，消息类型都属于一个特定的包。消息类型名总会包含一个斜杠,斜杠前面是包名。
> package-name/type-name 如 turtlesim/Color

### 编写ROS程序

创建功能包
catkin_create_pkg package-name
在那个目录下生成了两个配置文件。
	第一个文件,叫做 package.xml清单文件。
	第二个文件,叫做 CMakeLists.txt,是一个 Cmake 的脚本文件

编辑依赖depend

```
find_package(catkin REQUIRED COMPONENTS roscpp)
<build_depend>roscpp</build_depend>
<exec_depend>roscpp</exec_depend>
```

package包
ROS 包命名规范,只允许使用小写字母、数字和下划线_,而且首字符必须是一个小写字母。

```
project(package_name)
可执行文件
add_executable(executable-name source-files)
add_dependencies(executable-name ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(executable-name ${catkin_LIBRARIES})
```

***\*pubvel.cpp\****

ROS 话题都与一个消息类型相关联。每一个消息类型都有一个相对应 C++头文件。

头文件的目的是定义一个 C++类,此类和给定的消息类型含有相同的数据类型成员。这个类定义在以包名命名的域名空间中。 使用双分号(::)来区分开包名和类型名,双分号也称为范围解析运算符。

头文件#include <geometry_msgs/Twist.h>定义了一个名为geometry_msgs::Twist 的类。

创建发布者对象，发布消息的实际工作是由类名为ros::Publisher的一个对象来完成的

```cpp
#include <package_name/type_name.h>  #include <ros/ros.h>是一个实用的头文件，它引用了 ROS 系统中大部分常用的头文件。
#include <std_msgs/String.h> //这引用了 std_msgs/String 消息, 它存放在std_msgs package里，是由String.msg文件自动生成的头文件
#include <geometry_msgs/Twist.h>#(名为 geometry_msgs 的包所拥有的类型为 Twist 的消息)
这个头文件的目的是定义一个C++类,此类和给定的消息类型含有相同的数据类型成员。
node节点
ros::init ( argc , argv , "node_name" ) ;//初始化节点
ros::NodeHandle nh;//句柄，命名空间
这个类定义在以包名命名的域名空间中。这样命名的实际影响是当引用 C++代码中的消息类时,你将会使用双冒号(::)来区分开包名和类型名,双冒号也称为范围解析运算符。
ros::Publisher pub = node_handle.advertise<message_type>(topic_name, queue_size);
ros::Publisher pub = nh.advertise<geometry_msgs::Twist>("turtle1/cmd_vel",1000);
node_handle：ros::NodeHandle 类的一个对象
advertise：node_handle对象的方法
<message_type>：模板参数,是我们要发布的消息的数据类型
topic_name：是一个字符串,话题的名称。1000是消息序列的大小
时间间隔ros::Time、ros::Duration、定时器ros::Timer&ros::Rate
ros::Rate rate(n);//ros::Rate对象控制循环运行速度,以赫兹(Hz)为单位
rate.sleep(); //邻近每次循环迭代的结尾,我们调用此对象的 sleep 方法就会在程序中产生延迟
节点是否停止工作的检查
while (ros::ok()) {
geometry_msgs::Twist msg;//定义一个消息对象，给数据成员赋值；
//查看消息类型 rosmsg info */* 先用tab补全查看所有对象，再看成员名称
pub.publish(msg);}
```



订阅 turtlesim_node发布的/turtle1/pose 话题（turtlesim_node还发布另一个/turtle1/color_sensor）
回调函数
订阅者节点无法知道消息什么时候到达。为了应对这一事实,我们必须把响应收到消息事件的代码放到回调函数里,ROS 每接收到一个新的消息将调用一次这个函数。

```cpp
void function_name(const package_name::type_name &msg){. . .}
void pose_received ( const turtlesim::Pose &msg ) { }
ros::Subscriber sub = node_handle.subscribe(topic_name,queue_size, pointer_to_callback_function);
ros::Subscriber sub = nh.subscribe( "turtle1/pose" ,1000, &pose_received ) ;
ros::spin();//ros::spinOnce(); 消息订阅函数专用，ROS消息回调处理函数
```

***\*计算图源命名（命名规则）\****

节点、话题、服务和参数统称为计算图源名称(graph resource name)

节点名 /node_name ; /turtlesim

话题名 /node1/topic_name ; /turtle1/cmd_vel

> 全局名称：在任何地方(译者注:包括代码、命令行工具、图形界面工具等的任何地方)都可以使用的唯一名称。
> 前斜杠“/”表明这个名称为全局名称。
> 由斜杠分开的一系列命名空间(namespace),每个斜杠代表一级命名空间。命名空间用于将计算图源归类在一起。
>
> 相对名称(ralative graph resource name),相对名称的典型特征是它缺少全局名称带有的前斜杠“/”。
> 如果不知道 ROS 解析某个计算图源时所使用的默认命名空间,相对名称并不能和特定计算图源匹配。
>
> 设置默认命名空间
> 为节点选择一个不同的默认命名空间的最好也是最常用的方法是在启动文件中使用命名空间(ns)属性
> 此参数将为程序指定一个默认命名空间。_ _ns:=default-namespace
> 相对名称的目的
> 真正意义在于它使得在小系统基础上实现复杂系统变得更加容易。
> 使用相对名称时,这本质上给用户提供了一种非常简单的移植手段。除非一些特殊情况有特殊要求,否则编写节点时并不推荐使用全局名称。
> 私有名称
> 私有名称,以一个波浪字符(~)开始,是第三类也是最后一类计算图源名称。与相对名称的主要差别在于,私有名称不是用当前默认命名空间,而是用的它们节点名称作为命名空间。
> 私有名称常常用于参数——roslaunch 有专门的功能用于设置私有名称可以访问的的参数
> 匿名名称(Anonymous names)
> 一般用于为节点命名。匿名名称的目的是使节点的命名更容易遵守唯一性的规则。
> ros::init(argc, argv, base_name, ros::init_options::AnonymousName); //第四个参数



### 第6章 启动文件(launch file)

利用启动文件一次性配置和运行多个节点。
在一个XML格式的文件内将需要同时启动的一组节点罗列出来

```
roslaunch package-name launch-file-name
roslaunch agitr example.launch
roslaunch -v agitr example.launch //请求详细信息(Requesting verbosity)
```

roslaunch 首先会判断 roscore 是否正在运行;如果没有,则自动启动 roscore。

文件内所有的节点几乎都在同一时刻启动。因此,事实上你无法确定各个节点的启动顺序。

顺序影响的节点需要进行重新设计,从而克服启动顺序的约束

### 创建启动文件

插入根元素

```
<launch>
	...
</launch>
```

启动节点

启动节点

```
<node
    pkg=”package_name”
    type=”executable_name”
    name=”node_name”
    output=”screen” //输出
    respawn=”true” //可靠性
    required=”true” //必要节点
    launch-prefix="xterm -e" //小窗口
    ns=”namespace” //空间多开respawn="true"
/>
```

> pkg 和 type 属性定义了运行哪个程序来启动这个节点。这些和 rosrun 的两个命令行参数的作用是一致的
> name 属性给节点指派了名称,它将覆盖任何通过调用 ros::int来赋予节点的名称。
> screen 命令行选项来令 roslaunch 在控制台中显示所有节点的输出
> roslaunch会监视每一个节点,可以设置 respawn 为真,这样当节点停止的时候,roslaunch 会重新启动该节点。
> 必要节点(requiring node) 当一个必要节点终止的时候,roslaunch 会终止所有其他活跃节点并退出。
> respawn 和 required 二者的作用是相互矛盾的
> 为节点维护独立的窗口，对节点元素使用启动前缀(launch-prefix)属性
> launch-prefix=“command-prefix”
> xterm 命令将打开一个简单终端窗口。参数-e告诉 xterm 在新打开的终端中执行该命令行的剩余部分

roslaunch启动launch语法，include file 标签用法

```html
launch语法
<include file="$(find package-name)/launch-file-name" />
<include file="$(find probot_anno_moveit_config)/launch/planning_context.launch">  </include>

```



---

## 机器人操作系统（ROS）浅析  [美] Jason M. O'Kane 著 肖军浩译

### A Gentle Introduction to ROS

ROS能够提供类似传统操作系统的诸多功能，如硬件抽象、底层设备控制、常用功能实现、进程间消息传递和程序包管理等。它还提供相关工具和库，用于获取、编译、编辑代码以及在多个计算机之间运行程序完成分布式计算。 

***\*第 2  章 入门概述\****

2.1 安装 ROS

```
sudo apt-get install ros-kinetic-desktop-full
sudo apt-get install ros-kinetic-turtlesim
```

catkin编译系统（Build Systems）

设置环境变量  ROS要依据一些环境变量来定位文件。

```
gedit ~/.bashrc
source ~/.bashrc

sudo gedit /opt/ros/kinetic/setup.bash
source /opt/ros/kinetic/setup.bash
```

编辑账户根目录中的文件.bashrc，并在最下面添加前文的 source 命令

***\*第\*******\*3 章 编写ROS 程序\****

***\*3.1 创建工作区和功能包\****

```
catkin_create_pkg package-name
```

创建了一个存放这个功能包的目录，并在那个目录下生成了两个配置文件。

第一个配置文件，叫做 package.xml

第二个文件，CMakeLists.txt，是一个 Cmake 的脚本文件

ROS 包的命名规范，只允许使用小写字母、数字和下划线，而且首字符必须是小写字母。

hello.cpp

```
ros::init() #函数初始化ROS客户端库
ros::NodeHandle #创建此对象会将你的程序注册为ROS节点管理器的节点。
ROS_INFO_STREAM() #宏将生成一条消息，且这一消息被发送到不同的位置，包括控制台窗口
```

***\*3.2.2 编译 Hello 程序\****

ROS的catkin编译系统来处理。一共有四个步骤

***\*声明依赖库\**** 声明程序所依赖的其他功能包。

CMakeLists.txt 文件。

```
find_package(catkin REQUIRED)
```

package.xml

```
<build_depend>package-name</build_depend>
<run_depend>package-name</run_depend>
```

***\*声明可执行文件\****

CMakeLists.txt 中添加两行，来声明我们需要创建的可执行文件。

```
add_executable(executable-name source-files) 
#声明了我们想要的可执行文件的文件名，以及生成此可执行文件所需的源文件列表

target_link_libraries(executable-name ${catkin_LIBRARIES}) 
#告诉 Cmake 当链接此可执行文件时需要链接哪些库（在上面的 find_package 中定义）。
```

***\*编译\**** ***\*工作区\**** 编译所有包中的所有可执行文件：

```
catkin_make
```















