## F710控制turtlesim

ubuntu下使用 手柄控制ROS中的多个小乌龟turtlesim #测试运行成功
[quote](https://blog.csdn.net/answerMack/article/details/89365769)

安装手柄驱动包#设为Direct 模式

```
sudo apt install ros-kinetic-joy
sudo apt install ros-kinetic-joystick-drivers
```

### 查看手柄数据

```shell
ls /dev/input/   #js0sudo jstest /dev/input/js0
sudo jstest /dev/input/js0

Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 
Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 

```

![image-20201225093511956](https://i.loli.net/2020/12/25/Ja2BXeSPF9YUGCn.png)

## joy节点

```
roscore
rostopic list -v #/turtle1/cmd_vel [geometry_msgs/Twist]#话题/消息[消息类型]
rosmsg show sensor_msgs/Joy
rosmsg show geometry_msgs/Twist


rosrun joy joy_node
rostopic echo /joy

joy消息类型
---
header: 
  seq: 510
  stamp: 
    secs: 1607992000
    nsecs: 184356268
  frame_id: ''
axes: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0] #六个轴
buttons: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0] #12个键

```

```shell
#手柄
rosrun joy joy_node
rostopic  echo  /joy

#查询三连
rosnode info /joy_node
rostopic info /joy
rosmsg info sensor_msgs/Joy
```



```shell
#sudo jstest /dev/input/js0

#catkin_cpp
roslaunch joystick_example example.launch

#python
chmod +x joytwist.py
roslaunch joytwist joytwist.launch


```

借用geometry_msgs::Twist的数据

```
rosmsg info geometry_msgs/Twist
---
geometry_msgs/Vector3 linear
  float64 x //
  float64 y //
  float64 z //
geometry_msgs/Vector3 angular
  float64 x //
  float64 y //
  float64 z //
```

> [ERROR] [1608195597.784586]: bad callback: <bound method MoveitJoy.joyCB of <moveit_ros_visualization.moveitjoy_module.MoveitJoy instance at 0x7f8c681b7c68>>
> Traceback (most recent call last):
>   File "/opt/ros/kinetic/lib/python2.7/dist-packages/rospy/topics.py", line 750, in _invoke_callback   cb(msg)
>   File "/opt/ros/kinetic/lib/python2.7/dist-packages/moveit_ros_visualization/moveitjoy_module.py", line 475, in joyCB
>     raise Exception("Unknown joystick")
> Exception: Unknown joystick

---

### teleoperation遥控

```
roscore
rosrun turtlesim turtlesim_node
rosrun turtlesim turtle_teleop_key
```

```
sudo apt-get install ros-kinetic-rosserial-arduino
sudo apt-get install ros-kinetic-rosserial
rospack profile

sudo apt remove  --purge ros-kinetic-rosserial-arduino
sudo apt remove  --purge ros-kinetic-rosserial
```

---

http://wiki.ros.org/joy

Logitech Wireless Gamepad F710 (DirectInput Mode) 

![img](https://i.loli.net/2020/12/15/jVtnG3LqxNo6Kms.png)

![img](https://i.loli.net/2020/12/15/jfnNWKl8h9kwc4F.png)

![img](https://i.loli.net/2020/12/19/v2itFNISBVfQXDh.png)

Table of index number of /joy.buttons: 手柄按键索引号

| Index | Button name on the actual controller | 数值     |      |
| ----- | ------------------------------------ | -------- | ---- |
| 0     | X                                    | on / off |      |
| 1     | A                                    | on / off |      |
| 2     | B                                    | on / off |      |
| 3     | Y                                    | on / off |      |
| 4     | LB                                   | on / off |      |
| 5     | RB                                   | on / off |      |
| 6     | LT                                   | on / off |      |
| 7     | RT                                   | on / off |      |
| 8     | back                                 | on / off |      |
| 9     | start                                | on / off |      |
| 10    | Button stick left                    |          |      |
| 11    | Button stick right                   |          |      |

Table of index number of /joy.axes: Axes:  模拟量 -32767～+32767 (2^16)

| Index | Axis name on the actual controller    | 数值              | 方向     |
| ----- | ------------------------------------- | ----------------- | -------- |
| 0     | Left/Right Axis stick left（左摇杆）  | -32767~+32767     | （右正） |
| 1     | Up/Down Axis stick left（左摇杆）     | -32767~+32767     | （下正） |
| 2     | Left/Right Axis stick right（右摇杆） | 32767~+32767      | （右正） |
| 3     | Up/Down Axis stick right（右摇杆）    | 32767~+32767      | （下正） |
| 4     | cross key left/right（左方向键）      | -32767  0  +32767 | （右正） |
| 5     | cross key up/down（左方向键）         | -32767  0  +32767 | （下正） |





