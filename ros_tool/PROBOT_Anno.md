## 安装PROBOT_Anno

### moveit全家桶

```shell
$ sudo apt-get install ros-kinetic-moveit-*
ros-kinetic-moveit-setup-assistant

sudo apt-get install ros-kinetic-moveit-visual-tools
sudo apt-get install ros-kinetic-industrial-robot-simulator
sudo apt-get install ros-kinetic
easy-handeye
```

sudo gedit /etc/apt/sources.list

ResourceNotFound: industrial_robot_simulator

bash: /home/akingse/WORKSPACE_PATH/install/setup.bash: No such file or directory

```
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
echo "source ~/probot_anno_ws/devel/setup.bash" >> ~/.bashrc
gedit ~/.bashrc
source ~/.bashrc
```

## PROBOT Anno

[github](https://github.com/ps-micro/PROBOT_Anno)

源代码安装并编译

```
cd ~/catkin_ws/src
git clone https://github.com/ps-micro/PROBOT_Anno

ROS_VERSION=`/usr/bin/rosversion -d`   
sudo apt-get install ros-${ROS_VERSION}-moveit-*   
sudo apt-get install ros-${ROS_VERSION}-industrial-*   
sudo apt-get install ros-${ROS_VERSION}-gazebo-ros-control   
sudo apt-get install ros-${ROS_VERSION}-ros-control ros-${ROS_VERSION}-ros-controllers   
sudo apt-get install ros-${ROS_VERSION}-trac-ik-kinematics-plugin   
sudo apt-get install ros-${ROS_VERSION}-usb-cam 
```



---

之前对MoveIt的印象一直停留在使用Rviz拖动机械臂模型，然后再点击“plan”实现轨迹的规划，点击“execute”执行机械臂的运动这种比较浅层的功能。实际我们在控制机械臂运动的时候大都是通过编程的方式控制，而不是Rviz的图形化控制。

### MoveIt编程实现关节空间机械臂运动(正运动学)

[启用moveit](https://www.guyuehome.com/17267)

```shell
roslaunch probot_bringup probot_anno_bringup.launch sim:=true
#roslaunch probot_anno_moveit_config demo_gazebo.launch
#roslaunch probot_grasping probot_anno_grasping_demo.launch

source devel/setup.bash
#rosrun probot_anno_demo probot_demo.py
---
#roslaunch probot_anno_moveit_config demo.launch #moveit专用，勾选工具栏MotionPlanning
rosrun probot_anno_demo moveit_fk_demo.py
rosrun probot_anno_demo anno_fk_demo

```





---

### 工具包学习，古月居出品，PROBOT_Anno

```
使用现有launch
roslaunch setup_assistant.launch
```

![image-20210107165703396](https://i.loli.net/2021/01/07/Dks7yXxp4nrIAFm.png)

![image-20210107182132845](https://i.loli.net/2021/01/07/Mwk6xIoh8LeO9gV.png)

![image-20210107182207617](https://i.loli.net/2021/01/07/HAT3OXg4LUhqtcD.png)

![image-20210107182232991](https://i.loli.net/2021/01/07/T4ZFXoWdv5MVrCO.png)

![image-20210107182256336](https://i.loli.net/2021/01/07/x2vG6OiZJQAk41N.png)

![image-20210107182400410](https://i.loli.net/2021/01/07/gSIQ9V65eUET14q.png)

```
roscd probot_description
```

![image-20210107184533806](https://i.loli.net/2021/01/07/765zIsdhMcv4NbT.png)

> Some files have been modified outside of the Setup Assistant (according to timestamp). The Setup Assistant will not overwrite these changes by default because often changing configuration files manually is necessary, but we recommend you check the list and enable the checkbox next to files you would like to overwrite. 
> Attention: Some files (marked red) are changed both, externally and in Setup Assistant.

---







```
roslaunch marm_moveit_config demo.launch

rosrun marm_planning moveit_fk_demo.py
# python /home/akingse/tempopkg_ws/src/marm/marm_planning/scripts/moveit_fk_demo.py


rosrun marm_planning moveit_cartesian_demo.py _cartesian:=True
rosrun marm_planning moveit_cartesian_demo.py _cartesian:=False


```

![image-20201217142839538](https://i.loli.net/2021/01/07/hLIaZKFAYyTt7MP.png)

Unable to connect to move_group action server 'move_group' within allotted time (5s)

MotionPlanning - Trajectory Slider 永久循环



对比python与CPP

![image-20210106213922306](https://i.loli.net/2021/01/07/nUV1dNWBkA8mi2G.png)

![image-20210106214016004](https://i.loli.net/2021/01/07/uSK4pmCsW3AMlEB.png)

![image-20210106215158721](https://i.loli.net/2021/01/07/8LXiTn5mcvIAp2k.png)









