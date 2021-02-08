## 功能包 joyrasio

使用罗技F710接树莓派4B，控制数字量IO继电器；

```
rosrun package exec_name
```

节点名==可执行文件名\==源文件名

src/*.cpp->ros::init(argc,argv,"node_name") 
CMakeLists->add_executable(exec_name src/*.cpp) 

### 添加依赖

```
sensor_msgs joy geometry_msgs roscpp rospy std_msgs message_generation
```



---

## ROS package

```
source devel/setup.bash
rosrun joyrasio joy_demo_pub
rosrun joyrasio joy_demo_sub

rosrun joyrasio logi_joy
rosrun joyrasio serial_demo
```







---

### 飞快的小乌龟

```
roscore
rosrun turtlesim turtlesim_node
rosrun turtlesim turtle_teleop_key

rosrun joystick_example example

roslaunch joystick_example example.launch

```

![image-20201226170246184](https://i.loli.net/2020/12/26/bvWDdjpSiaXeJf6.png)