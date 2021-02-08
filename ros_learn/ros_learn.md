## 记录2020-Ubuntu

二进制包vs源代码包

|      | 二进制            | 源代码            |
| ---- | ----------------- | ----------------- |
| 安装 | apt-get install   | git clone github  |
| 位置 | /opt/ros/kinetic/ | ~/catkin_ws/src   |
| 编译 | -                 | cmake/catkin_make |
| 来源 | 官方apt源         | 开源              |

### catkin_make注意

找不同

```cpp
ros::Publisher person_info_pub = n.advertise<learning_topic::Person>("/person_info", 10);
ros::Publisher person_info_pub = n.advertise<learning_topic::Person>("person_info", 10);    
```

```cmake
#三个缺一不可
add_executable(person_publisher src/person_publisher.cpp)
add_dependencies(person_publisher learning_topic_generate_messages_cpp)
target_link_libraries(person_publisher ${catkin_LIBRARIES})

#相同的代码，莫名的bug，严重怀疑ros更新代码规范管理变得更加严格，以致于语法发生了变化；
#经过这一周与bug的斗争，使我回忆起了ros的知识；
```



---



### catkin_workspace  #ROS工作空间文件系统

![image-20201210170309695](https://i.loli.net/2020/12/10/tByhmYOep21DSaw.png)



## ros::ok()
ros::spin(); ros::spinOnce() 区别
ros::spinOnce()函数顺序执行一次，尤其是我想控制接收速度的时候。配合ros::ok()效果极佳。
//ros::spin()用于调用所有可触发的回调函数。将进入循环，不会返回，类似于在循环里反复调用ros::spinOnce()。



## Time与Duration

#include<ros/time.h> 和 #include<ros/duration.h>
一种是时刻(ros::Time),一种是时长(ros::Duration)。Time和Duration表示的概念并不相同,Time指的是某个时刻,而Duration指的是某个时段。
sleep
roscpp中提供了两种sleep的方法:
ros::Duration(0.5).sleep();//用Duration对象的sleep方法休眠
ros::Rater(10); r.sleep(); //10HZ
Timer
ROS中的定时器Timer,它是通过设定回调函数和触发时间来实现某些动作的反复执行
ros::Timer timer1=n.createTimer(ros::Duration(0.1), callback1);//timer1每0.1s触发一次callback1函数



---

## 与bug作斗争

### catkin_make编译错误

不是在解决bug就是在解决bug的路上；

> CMake Error at /opt/ros/kinetic/share/catkin/cmake/catkinConfig.cmake:83 (find_package):
>   Could not find a package configuration file provided by
>   "gazebo_ros_control" with any of the following names:
>
>     gazebo_ros_controlConfig.cmake
>     gazebo_ros_control-config.cmake
>
>   Add the installation prefix of "gazebo_ros_control" to CMAKE_PREFIX_PATH or  set "gazebo_ros_control_DIR" to a directory containing one of the above  files.  If "gazebo_ros_control" provides a separate development package or
>   SDK, be sure it has been installed.
> Call Stack (most recent call first):
> mbot_gazebo/CMakeLists.txt:10 (find_package)

### 缺少对应功能包

源码安装ROS软件包时经常会遇到一个问题 xxxx-config.cmake没有找到。这是由于这个软件包依赖于其他软件包，但是被依赖的软件包没有安装。

```shell
cd catkin_ws/src
git clone https://github.com/ros-drivers/velodyne
cd .. #去对应工作空间下操作
rosdep install --from-paths src --ignore-src -r -y
#好像删多了
rosdep install --from-paths src --ignore-src --rosdistro=kinetic -y


```

### ROS环境变量

> - ros_controllers/ackermann_steering_controller
> - ros_demo_control/src/ackermann_steering_controller
> Multiple packages found with the same name "combined_robot_hw":

```shell
echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
sudo gedit ~/.bashrc


sudo gedit /opt/ros/kinetic/setup.bash
# source /opt/ros/kinetic/setup.bash #只想改变当前终端下的环境变量

创建工作空间时catkin_make，以生层build和devel（setu.bash）
source devel/setup.bash
echo $ROS_PACKAGE_PATH
- /home/akingse/tempopkg_ws/src:/home/akingse/catkin_ws/src:/home/akingse/tutorial_ws/src:/opt/ros/kinetic/share

```




