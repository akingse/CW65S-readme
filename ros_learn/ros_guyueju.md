## 古月居 ROS21讲

ROS学习笔记 

文字紧接图片会居左（shift+enter）
![image-20201210104638610](https://i.loli.net/2020/12/10/jkisyeMonwZRKgO.png)

![image-20201210104649985](https://i.loli.net/2020/12/10/tplNgwG1Lb2CPaq.png)

**\*关于ROS变量环境\***

> .bashrc文件主要保存个人的一些个性化设置，如命令别名、路径等。实现环境变量配置，在操作系统中用来指定操作系统的一些参数。
>
> 最常见的环境变量 —— PATH，它的用途就是当用户要求系统运行一个程序而没有告诉它程序所在的完整路径时，系统除了在当前目录下寻找此程序外，还要到PATH变量中指定的路径去寻找。
>

打开一个终端，需要向工作区添加setup.bash文件，否则终端无法找到你的代码，解决方法：

```
sudo gedit ~/.bashrc #打开home目录下隐藏的.bashrc文件文件，添加
echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
source ~/.bashrc #重新编译，立即生效
```

ROS机器人系列 8章
![image-20201210105636642](https://i.loli.net/2020/12/10/UoxjPpnGAkSlhgN.png)

通信机制

> 话题通信机制
>
> 服务通信机制
>
> 参数通信机制

Talker/Listener注册→Master信息匹配→Talker/Listener连接请求

Talker→Master→Listener

---

 

ROS的特点

> 1、分布式的结构
>
> 一个进程在ros中称作一个节点（node），每个功能节点可以单独编译，节点之间形成点对点的通信，适合多机协同工作。
>
> 2、语言支持广泛
>
> 功能节点的接口与编程语言无关。支持C++、Python、Java等。
>
> 3、集成度高功能完备
>
> 集成了众多的开源项目，如OpenCV、pcl（point cloud library）等。
>
> 4、丰富的组件化工具
>
> 物理仿真环境gazebo，3d的数据可视化工具rviz，数据记录工具rosbag，Qt工具箱rqt_* 。
>
> 5、免费且开源
>
> 遵循BSD许可协议，可以随意修改并商用，功能包的数量迅速增加。
>



中文术语表

> Dependent Package 依赖包
>
> Build 构建
>
> Pose 位姿
>
> NodeHandle 节点句柄
>
> End Effector 末端执行器

---

### [古月居](https://www.guyuehome.com/category/column/ros-exploring/page/3)

![image-20201213223328804](https://i.loli.net/2020/12/17/8lGWdLCbYI6sVpT.png)



---

## 4.机器人仿真

### mbot package 三连

rosnode list

rosnode info /*

rostopic list
rostopic info /*
rosmsg info * 

```
roslaunch mbot_description arbotix_mbot_with_camera_xacro.launch
```

arbotix是一个基于ROS工具rviz的仿真模拟器。

sudo apt-get install ros-kinetic-arbotix

ResourceNotFound: turtlebot_teleop

```
sudo apt-get install ros-kinetic-turtlebot-teleop
sudo apt-get install ros-kinetic-turtlebot ros-kinetic-turtlebot-apps ros-kinetic-turtlebot-interactions ros-kinetic-turtlebot-simulator ros-kinetic-kobuki-ftdi ros-kinetic-ar-track-alvar-msgs
```

/home/akingse/tempopkg_ws/src/ttelep

![image-20201214192220758](https://i.loli.net/2020/12/20/nt4UIYfLN5G2guh.png)





![image-20201214192311543](https://i.loli.net/2020/12/20/B7StqZh4nA6jgO9.png)



![image-20201215100802642](https://i.loli.net/2020/12/20/KHbL7RaTgvqQ54Z.png)

监控话题 /cmd_vel

rostopic echo /cmd_vel

问题在于 turtlebot_teleop_joystick，吃了/joy，没有输出/cmd_vel

写一个节点，订阅手柄sensor_msgs/Joy，发布/cmd_vel，信息转换，

---

## [古月居官网](https://www.guyuehome.com/)

[ros探索总结](https://www.guyuehome.com/category/column/ros-exploring)

MoveIt编程实现[笛卡尔空间机械臂运动](https://www.guyuehome.com/17311)



轨迹插补，[轨迹重新定义](https://www.guyuehome.com/2933)









