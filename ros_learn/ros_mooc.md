## ***\*《机器人操作系统入门》\****

https://www.icourse163.org/course/ISCAS-1002580008

中国大学MOOC---《机器人操作系统入门》课程讲义.pdf

机器人操作系统入门.pdf ros-tutorial-icourse163.pdf //是同一个文档

---

***\*缺少依赖\****，找不到软件包

```
sudo apt-get install ros-kinetic-PACAKGE

Could not find a package configuration file provided by "controller_manager"

sudo apt-get install ros-kinetic-ros-control 

sudo apt-get install ros-kinetic-ros-controllers

sudo apt-get install ros-kinetic-controller-manager
```



> controller全家桶
>
> ros-kinetic-controller-manager
>
> ros-kinetic-controller-interface
>
> ros-kinetic-controller-manager-msgs
>
> ros-kinetic-controller-manager-tests
>
>  

```
cd /opt/ros/kinetic/share #注意安装位置

sudo apt remove  --purge ros-kinetic-controller-interface 
sudo apt remove  --purge ros-kinetic-controller-manager-msgs

\#sudo apt-get purge ros-kinetic-controller-manager

系统底层驱动工具包，安装在/opt/ros/kinetic/share，不要装在/home/akingse/catkin_ws/src下
```

***\*教学demo\****

功能包所在位置 /home/akingse/tutorial_ws/src/robot_sim_demo/launch

```
roslaunch robot_sim_demo robot_spawn.launch
rosrun robot_sim_demo robot_keyboard_teleop.py
```

![image-20201214100625979](https://i.loli.net/2020/12/14/TSm7zKuYNQBeCGj.png)



***\*编译\****

对于源代码包,我们只有编译才能在系统上运行。而Linux下的编译器有gcc、g++,随着源文件的增加,直接用gcc/g++命令的方式显得效率低下,人们开始用Makefile来进行编译。然而随着工程体量的增大,Makefile也不能满足需求,于是便出现了Cmake工具。CMake是对make工具的生成器,是更高层的工具,它简化了编译构建过程,能够管理大型项目,具有良好的扩展性。对于ROS这样大体量的平台来说,就采用的是CMake,并且ROS对CMake进行了扩展,于是便有了Catkin编译系统。

![image-20201214100836050](https://i.loli.net/2020/12/14/d2jYkB59LmEctNi.png)

gcc→Makefile(效率高)→CMake(工程体量大)→Catkin(ROS扩展)

一个Catkin的软件包(package)必须要包括两个文件:

package.xml: 包括了package的描述信息；

CMakeLists.txt: 构建package所需的CMake文件；

catkin编译的工作流程如下:

\1. 首先在工作空间 catkin_ws/src/ 下递归的查找其中每一个ROS的package。

\2. package中会有 package.xml 和 CMakeLists.txt 文件,Catkin(CMake)编译系统依据 CMakeLists.txt 文件,从而生成 makefiles (放在 catkin_ws/build/ )。

\3. 然后 make 刚刚生成的 makefiles等文件,编译链接生成可执行文件(放在catkin_ws/devel)。

 

一个package下常见的文件、路径有:

> CMakeLists.txt: 定义package的包名、依赖、源文件、目标文件等编译规则,是package不可少的成分
>
> package.xml: 描述package的包名、版本号、作者、依赖等信息,是package不可少的成分
>
> src/: 存放ROS的源代码,包括C++的源码和(.cpp)以及Python的module(.py)
>
> include/: 存放C++源码对应的头文件
>
> scripts/: 存放可执行脚本,例如shell脚本(.sh)、Python脚本(.py)
>
> msg/: 存放自定义格式的消息(.msg)
>
> srv/: 存放自定义格式的服务(.srv)
>
> models/: 存放机器人或仿真场景的3D模型(.sda, .stl, .dae等)
>
> urdf/: 存放机器人的模型描述(.urdf或.xacro)
>
> launch/: 存放launch文件(.launch或.xml)

2.2 Pacakge组成

ros软件基本组织，catkin基本单元，包含多个节点

> cmakelists.txt，规定catkin编译的规则
>
> package.xml，定义package属性
>
> manifest.xml，老版本的写法，rosbuild专用
>
> 代码src（.cpp .py）include（.h）
>
> 脚本script（.py .sh）
>
> 自定义通讯（srv,msg,action）
>
> 多启动launch（.launch）
>
> 配置文件config（.yaml）

roslaunch文件

launch文件同样也遵循着xml格式规范,是一种标签文本,它的格式包括以下标签:

```
<launch>   <!--根标签-->

<node>   <!--需要启动的node及其参数-->

<include>   <!--包含其他launch-->

<machine>   <!--指定运行的机器-->

<env-loader>   <!--设置环境变量-->

<param>   <!--定义参数到参数服务器-->

<rosparam>   <!--启动yaml文件参数到参数服务器-->

<arg>   <!--定义变量-->

<remap>   <!--设定参数映射-->

<group>   <!--设定命名空间-->
```

---

demo演示

```
$ roslaunch robot_sim_demo robot_spawn.launch
```

> NODES
>
>  /xbot/
>
>   robot_state_publisher (robot_state_publisher/robot_state_publisher)
>
>   spawner (controller_manager/spawner)
>
>  /
>
>   cmd_vel_mux (nodelet/nodelet)
>
>   gazebo (gazebo_ros/gzserver)
>
>   gazebo_gui (gazebo_ros/gzclient)
>
>   mobile_base_nodelet_manager (nodelet/nodelet)
>
>   urdf_spawner (gazebo_ros/spawn_model)

```
$ rosnode list
/cmd_vel_mux
/gazebo
/gazebo_gui
/mobile_base_nodelet_manager
/rosout
/xbot/robot_state_publisher
rosnode info /cmd_vel_mux
rosrun robot_sim_demo robot_keyboard_teleop.py
rosrun image_view image_view image:=/camera/rgb/image_raw #查看摄像头模拟捕捉的画面
```

/rosout前面的反斜杠“/”表明该节点名称属于全局命名空间。之所以叫做全局名称因为它们在任何地方（包括代码、命令行工具、图形界面工具等的任何地方）都可以使用。无论这些名称用作众多命令行工具的参数还是用在节点内部，它们都有明确的含义。这些名称从来不会产生二义性，也无需额外的上下文信息来决定名称指的哪个资源。如/turtle1/cmd_vel 由斜杠分开的一系列命名空间（namespace），每个斜杠代表一级命名空间。命名空间用于将相关的计算图源（节点、话题、服务和参数统称为计算图源，而每个计算图源由一个叫计算图源名称（graph resource name）的短字符串识）归类在一起。

turtlesim

```
$ roscore
$ rosrun turtlesim turtlesim_node
$ rosrun turtlesim turtle_teleop_key
```

demo

```
$ roslaunch robot_sim_demo robot_spawn.launch
$ rostopic list
$ rostopic info /camera/rgb/image_raw #属性
rosrun image_view image_view image:=/camera/rgb/image_raw #rgb图像+
rosrun image_view image_view image:=/camera/depth/image_raw #深度图=点云
rosrun robot_sim_demo robot_keyboard_teleop.py
rosnode list
rosnode info /robot_teleop #名称变了，查看话题→
rostopic info /cmd_vel_mux/input/teleop #查看类型→
rostopic echo /cmd_vel_mux/input/teleop #具体实时变化
rosmsg info geometry_msgs/Twist # rosmsg info查看具体定义
rostopic pub -1 /cmd_vel_mux/input/teleop geometry_msgs/Twist -- '[10.0, 0.0, 0.0]' '[0.0, 0.0, 6.28]'
```

四大通信方式 ： topic service parameter(参数服务器) actionlib(动作库)

Topic 主题

Service 服务

Parameter Service 参数服务器

Actionlib 动作库

|          | topic                                      | service                    | param                | action       |
| -------- | ------------------------------------------ | -------------------------- | -------------------- | ------------ |
|          | 实时性、周期性，节点对节点，单向           | 临时而非周期性的通信，双向 | 参数服务器，静态字典 | 长时间通信， |
| 文件夹   | msg (message)                              | srv (server)               |                      |              |
| 文件     | .msg                                       | .srv                       | .yaml                |              |
|          | pub-sub到master注册，pub发布topic，sub订阅 | client-serverrequest→reply |                      |              |
|          | rostopic list                              | rosservice list            | rosparam list        |              |
|          | rostopic info * (type)                     | rosservice info *          |                      |              |
| 自定义   | rostopic pub                               | rosservice call            |                      |              |
|          |                                            |                            |                      |              |
| 数据类型 | message                                    | server                     |                      |              |
|          | rosmsg list/show                           | rossrv list/show           |                      |              |

---

**第五课** ***\*常用工具\****

rosbridge moveit!专用工具

gazebo是一种最常用的ROS仿真工具,也是目前仿真ROS效果最好的工具;RViz是可视化工具,是将接收到的信息呈现出来;rqt则是非常好用的数据流可视化工具,有了它我们可以直观的看到消息的通信架构和流通路径;rosbag则是对软件包进行操作的一个命令,此外还提供代码API,对包进行操作编写。rosbridge是一个沟通ROS和外界的功能包,moveit!是目前为止应用最广泛的开源操作软件。

 

***\*5.1 Gazebo\*******\*仿真\****

ODE物理引擎。vrep，vbots，carsim

roslaunch robot_sim_demo robot_spawn.launch

仿真不仅仅只是做出一个很酷的3D场景,更重要的是给机器人一个逼近现实的虚拟物理环境,比如光照条件、物理距离等等。

通常一些不依赖于具体硬件的算法和场景都可以在Gazebo上仿真,例如图像识别、传感器数据融合处理、路径规划、SLAM等任务完全可以在Gazebo上仿真实现,大大减轻了对硬件的依赖。

 

***\*5.2 Rviz\*******\*可视化\****

虽然从界面上来看,RViz和Gazebo非常相似,但实际上两者有着很大的不同,Gazebo实现的是仿真,提供一个虚拟的世界,RViz实现的是可视化,呈现接收到的信息。左侧的插件相当于是一个个的subscriber,RViz接收信息,并且显示。所以RViz和Gazebo有本质的差异。

the robot visualization tool 可视化工具

roslaunch robot_sim_demo robot_spawn.launch

rviz

add>>robotmodel,camera,laserscan

***\*5.3 Rqt\*******\*可视化\*******\*(ros qt)\****

$ rqt_graph,显示通信架构

$ rqt_plot,绘制曲线

$ rqt_console，查看日志

---

***\*第六课 roscpp\****

6.1 Client Library与roscpp（C++版本）

ROS的***\*客户端库(Client\**** ***\*Libarary)\**** 类似高级API ，封装底层接口。

ROS为机器人开发者们提供了不同语言的***\*编程接口(Client\**** ***\*Libarary)\****,ros提供了多个版本， 比如C++接口叫做roscpp,Python接口叫做rospy,Java接口叫做rosjava。尽管语言不通,但这些接口都可以用来创建topic、service、param,实现ROS的通信功能。

roscpp执行效率高；rospy开发效率高；

 

整个ROS包括的packages

![image-20201214102403747](https://i.loli.net/2020/12/14/iYyetVZWfRXo5SM.png)

调用ROS的C++接口,首先就需要  #include <ros/ros.h>  。
roscpp的主要部分包括:

```
ros::init(); ros::NodeHandle n;: //解析传入的ROS参数,，为本node命名。
::作用域限定符，init()函数在ros命名空间中
ros::NodeHandle : 和topic、service、param等交互的公共接口。句柄，创建调用
ros::NodeHandle是一个class类，内含成员函数，成员变量，成员函数有 advertise(),subscribe()
ros::Publisher pub = nh.advertise<topic_demo::gps>("gps_info", 1);
ros::Subscriber sub = nh.subscribe("gps_info", 1, gpsCallback);
ros::master : 包含从master查询信息的函数
ros::this_node:包含查询这个进程(node)的函数
ros::service:包含查询服务的函数
ros::param:包含查询参数服务器的函数,而不需要用到NodeHandle
ros::names:包含处理ROS图资源名称的函数
```

> 以上功能可以分为以下几类:
> Initialization and Shutdown 初始与关闭
> Topics 话题Services 服务
> Parameter Server 参数服务器
> Timers 定时器
> NodeHandles 节点句柄
> Callbacks and Spinning 回调和自旋
> Logging 日志
> Names and Node Information 名称管理
> Time 时钟
> Exception 异常
>