## topic标准节点

### python节点

```shell
python /home/akingse/catkin_ws/src/joyrasio/src/joypy_demo_pub.py
python /home/akingse/catkin_ws/src/joyrasio/src/joypy_demo_sub.py
rosrun joyrasio joypy_demo_pub.py
rosrun joyrasio joypy_demo_sub.py

#权限
sudo chmod +x scripts.py
#在CMakeLists中添加：
install(PROGRAMS 
   scripts/your_scripts.py 
   DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

使用cpp-stringstream打印输出

```c
数字,字符串
    
ROS_INFO();
ROS_INFO("linear:%.3lf angular:%.3lf",v.linear.x,v.angular.z); 
ROS_INFO(“s%”, msg.data.c_str()),输出一个字符串变量
ROS_INFO(“I heard: [%s]”, msg.data.c_str()),输出一个字符串变量，这里的中括号不是必须的，输出时会直接显示这个中括号
ROS_INFO(“I heard: [%s]”, msg->data.c_str()),输出一个指针变量
ROS_INFO(“Publish Person Info: name:%s age:%d sex:%d”,person_msg.name.c_str(), person_msg.age, person_msg.sex)，按数据类型输出


ROS_INFO_STREAM();
ROS_INFO_STREAM(“Hello ROS”),输出字符串
ROS_INFO_STREAM("Send"<<"linear="<<msg.linear.x<<"angular="<<msg.angular.z);




```

### 标准发布

```cpp
int main(int argc, char *argv[])
{
	ros::init(argc, argv, "joy_demo_pub");
	ros::NodeHandle n;
	ros::Publisher chatter_pub = n.advertise<std_msgs::String>("chatter", 1000);
	ros::Rate loop_rate(10);
	int count = 0;
	while (ros::ok())
	{
		std_msgs::String msg;
		std::stringstream ss;//发字符串
		ss << "hello world " << count;
		msg.data = ss.str(); //数字转字符；
		ROS_INFO_STREAM("pub"<<msg.data);

		chatter_pub.publish(msg);
		ros::spinOnce();
		loop_rate.sleep();
		++count;
	}
}
```

### 标准订阅

```cpp
void chatterCallback(const std_msgs::String &msg)
{
	ROS_INFO_STREAM("I heard:"<<msg.data);
}

int main(int argc, char *argv[])
{
	ros::init(argc, argv, "joy_demo_sub");
	ros::NodeHandle n;
	ros::Subscriber sub = n.subscribe("chatter", 1000, chatterCallback);
	ros::spin();
	return 0;
}
```

### py发布

```python
import rospy
from std_msgs.msg import String

def talker():
    pub = rospy.Publisher('chatter', String, queue_size=10)
    rospy.init_node('joypy_demo_pub')
    rate = rospy.Rate(10) # 10hz
    while not rospy.is_shutdown():
        hello_str = "hello world " + str(rospy.get_time())
        rospy.loginfo(hello_str)
        pub.publish(hello_str)
        rate.sleep()
        
if __name__ == '__main__':
    try:
        talker()
    except rospy.ROSInterruptException:
        pass
```

### py订阅

```python
import rospy
from std_msgs.msg import String

def callback(data):
    rospy.loginfo(rospy.get_caller_id() + " I heard " + data.data)

def listener():
    rospy.init_node('joypy_demo_sub') 
    rospy.Subscriber("chatter", String, callback)
    rospy.spin()

if __name__ == '__main__':
    listener()
```



## sub-pub

```cpp
#include<ros/ros.h>
#include<geometry_msgs/Twist.h>
#include<sensor_msgs/Joy.h>
#include<iostream>
//using namespace std;

class Sub_Pub{
	public:
		Sub_Pub(){
            pub = n.advertise<geometry_msgs::Twist>("/turtle1/cmd_vel",10);
			sub = n.subscribe<sensor_msgs::Joy>("joy", 10, &TeleopJoy::callBack, this);
        }
	private:
		void callback(const sensor_msgs::Joy::ConstPtr& joy);
		ros::NodeHandle n;
		ros::Publisher pub;
		ros::Subscriber sub;
};


void Sub_Pub::callback(const sensor_msgs::Joy::ConstPtr& joy){	
	geometry_msgs::Twist orien;
	orien.angular.z = joy->axes[0];
	orien.linear.x = joy->axes[1];
}

int main(int argc, char** argv)
{
	ros::init(argc, argv, "sub_pub_demo");
	Sub_Pub teleop_turtle;
	ros::spin();
}

```

