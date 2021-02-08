

## ROS与Arduino

安装[arduino](https://www.ncnynl.com/archives/201610/918.html)

```
sudo apt-get install arduino
```

1. 二进制方式安装在ROS工作站(推荐)

```
sudo apt-get install ros-kinetic-rosserial-arduino
sudo apt-get install ros-kinetic-rosserial
rospack profile
```

> 0.027001   /opt/ros/kinetic/share
> 0.001012 * /opt/ros/kinetic/share/doc
> 0.000954 * /opt/ros/kinetic/share/doc/eigenpy
> 0.000804   /home/akingse/catkin_ws/
> 0.000573 * /opt/ros/kinetic/share/doc/eigenpy/doxygen-html
> 0.000388 * /home/akingse/catkin_ws/devel
> 0.000301   /home/akingse/catkin_ws/src
> 0.000180 * /home/akingse/catkin_ws/devel/share
> 0.000178 * /opt/ros/kinetic/share/OpenCV-3.3.1-dev
> 0.000137 * /home/akingse/catkin_ws/devel/lib
> 0.000119 * /opt/ros/kinetic/share/doc/eigenpy/doxygen-html/search
> 0.000067 * /opt/ros/kinetic/share/man
> 0.000044 * /home/akingse/catkin_ws/devel/share/joyrasio
> 0.000038 * /opt/ros/kinetic/share/OpenCV-3.3.1-dev/haarcascades
> 0.000038 * /home/akingse/catkin_ws/devel/share/joystick_example
> 0.000037 * /home/akingse/catkin_ws/devel/share/serial_port
> 0.000014 * /opt/ros/kinetic/share/OpenCV-3.3.1-dev/lbpcascades
> 0.000013 * /opt/ros/kinetic/share/man/man1
> 0.000013 * /opt/ros/kinetic/share/doc/eigenpy/doxygen-html/pictures
> 0.000012 * /home/akingse/catkin_ws/devel/lib/joyrasio



## ros-cpp控制舵机



```cpp
#include <ros/ros.h>
#include <std_msgs/Float64.h>
#include <std_msgs/Float64MultiArray.h>
#include <serialrial.h>
#include <boost/thread.hpp>

serial::Serial ser; //定义串口对象
char cmd_return[40] = ""; //全局舵机控制字符数组,长度为15*2+10

class MultiSubscribe {
public:
    MultiSubscribe();

    ~MultiSubscribe();

    std_msgs::Float64MultiArray joint_angle;
    std_msgs::Float64 control_interval;

    void callback_angle(const std_msgs::Float64MultiArray::ConstPtr &msg_angle);

    void callback_interval(const std_msgs::Float64::ConstPtr &msg_interval);

private:
    ros::NodeHandle n_;
    ros::Subscriber sub_angle_;
    ros::Subscriber sub_interval_;

    int joint_n; //正交关节对数
};
```









