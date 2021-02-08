BYO自带 Bring Your Own

Own Toolbox

## roslaunch

```
<node>
<param>/<rosparam>
<arg>
<remap>
<include>

```

## tf

```
sudo apt-get install ros-kinetic-turtle-tf
roslaunch turtle_tf turtle_tf_demo.launch
rosrun turtlesim turtle_teleop_key
rosrun tf view_frames

rosrun tf tf_echo turtle1 turtle2
rosrun rviz rviz -d `rospack find turtle_tf` /rviz/turtle_rviz.rviz

```

## rqt

```
rqt_console
rqt_graph
rqt_plot

```

![image-20201209151441610](https://i.loli.net/2020/12/09/yR3pS7iuEo1hsqT.png)

## RViz

![image-20201209153424639](https://i.loli.net/2020/12/09/miNo6sPcuqdQFnO.png)

## Gazebo



![image-20201209154534181](https://i.loli.net/2020/12/09/HhYdZbyKCFqAsMQ.png)

---

## moveit与机械臂控制

URDF一种使用xml格式描述的机器人模型文件

<links>：坐标系与几何关系

```xml
<link name="<link name>">描述机器人刚体的外观和物理属性
	<inertial>...</inertial>外观参数
	<visual>...</visual>惯性参数
	<collision>...</collision>碰撞参数
</link>
```

<joints>：links之间的连接关系

```xml
运动学和动力学
  <joint    name="joint9"    type="revolute">
    <origin      xyz="0.08 0 0"      rpy="-1.5708 0 0" />
    <parent      link="Link8" />
    <child      link="Link9" />
    <axis      xyz="0 0 1" />
    <limit      lower="-3.14"      upper="3.14"      effort="100"      velocity="3" />
  </joint>

parents frame
child frame
joint origin
joint axis
```

![image-20201209164404619](https://i.loli.net/2020/12/09/5Jb8ZKoDWhvdG41.png)

urdf的进阶版本 xacro模型文件

<robot> 模型的顶层文件

连杆-关节-连杆

link-joint-link



```m
<xacro:include filename="myRobot.xacro"/>
```

```
<materrial name="balck">
	<color=rgba="0 0 0 1"/>
</materrial>
```

---

六自由度机械臂SolidWorks模型转化成urdf文件，添加简单gazebo属性并修改为xacro

> SolidWorks出了一款sw_urdf_exporter插件，可以自动生成urdf及展示用的launch文件；
>
> 需要手动添加轴和坐标系，然后手动命名并在插件中设定；
>
> 新建dofninet_description.urdf.xacro文件

```
<?xml version="1.0"?>
<robot name="myrobot_description" xmlns:xacro="http://www.ros.org/wiki/xacro">
……
原myrobot_description.urdf文件的内容
……
 <!--/// gazebo -->
      <!-- Transmissions for ROS Control -->
    <xacro:macro name="transmission_block" params="joint_name">
        <transmission name="tran1">
            <type>transmission_interface/SimpleTransmission</type>
            <joint name="${joint_name}">
                <hardwareInterface>hardware_interface/PositionJointInterface</hardwareInterface>
            </joint>
            <actuator name="motor1">
                <hardwareInterface>hardware_interface/PositionJointInterface</hardwareInterface>
                <mechanicalReduction>1</mechanicalReduction>
            </actuator>
        </transmission>
    </xacro:macro>
    
    <xacro:transmission_block joint_name="base_link_to_link_02"/>
    <xacro:transmission_block joint_name="link_02_to_link_03"/>
    <xacro:transmission_block joint_name="link_03_to_link_04"/>
    <xacro:transmission_block joint_name="link_04_to_link_05"/>
    <xacro:transmission_block joint_name="link_05_to_link_06"/>
    <xacro:transmission_block joint_name="finger_joint"/>

    <!-- ros_control plugin -->
    <gazebo>
        <plugin name="gazebo_ros_control" filename="libgazebo_ros_control.so">
            <robotNamespace>/myrobot_description</robotNamespace>
        </plugin>
    </gazebo>

</robot>
```

launch

```
<launch>
  <arg
    name="urdf_file" default="$(find xacro)/xacro.py '$(find myrobot_description)/urdf/myrobot_description.urdf.xacro'" />
  <arg
    name="gui"
    default="True" />
  <param
    name="robot_description"
    command="$(arg urdf_file)" />
  <param
    name="use_gui"
    value="$(arg gui)" />
  <node
    name="joint_state_publisher"
    pkg="joint_state_publisher"
    type="joint_state_publisher" />
  <node
    name="robot_state_publisher"
    pkg="robot_state_publisher"
    type="state_publisher" />
  <node
    name="rviz"
    pkg="rviz"
    type="rviz"
    args="-d $(find myrobot_description)/urdf.rviz" />
</launch>
```

#### Arbotix

> Arbotix是一款控制电机、舵机的控制板，并提供相应的ros功能包，但是这个功能包的功能不仅可以驱动真实的Arbotix控制板，它还提供一个差速控制器，通过接受速度控制指令更新机器人的joint状态，从而帮助我们实现机器人在rviz中的运动。
>
> arbotix配置文件格式为.yaml，通常放在模型包的config文件夹下。模拟仿真比较简单，一个launch文件+arbotix配置文件即可。该配置文件与控制器相关，定义控制器名称、作用的关节（关节一定要写全，不然会出现tf变换错误）以及位置速度参数等，具体可见本文代码。
>
> 需要特别注意的是，yaml格式比较严格，不能解析tab，要用空格来代替。写好之后可以利用这个地址[格式检查](https://www.bejson.com/validators/yaml/)来检查一下yaml是否有格式错误。

```yaml
source: myrobot_arm.yaml
baud: 1000000   #与实际有关，虚拟仿真时可以不用管
rate: 100	#与实际有关，虚拟仿真时可以不用管
port: /dev/ttyUSB0
read_rate: 15       #与实际有关，虚拟仿真时可以不用管
write_rate: 25      #与实际有关，虚拟仿真时可以不用管
joints: {
    joint1: {id: 1, max_angle: 135, min_angle: -135, max_speed: 90},
    joint2: {id: 2, max_angle: 135, min_angle: -135, max_speed: 90},
    joint3: {id: 3, max_angle: 135, min_angle: -135, max_speed: 90},
    joint4: {id: 4, max_angle: 135, min_angle: -135, max_speed: 90},
    joint5: {id: 5, max_angle: 135, min_angle: -135, max_speed: 90},
    finger_joint1: {id: 6, max_speed: 90},
}
controllers: {
    arm_controller: {type: follow_controller, joints: [joint1, joint2, joint3, joint4, joint5], action_name: arm_controller/follow_joint_trajectory, onboard: False }
}
```







---

[Moveit输出规划轨迹到Gazebo](https://blog.csdn.net/yaked/article/details/51436262)

创建一个从MoveIt！到Gazebo的控制文件controllers.yaml，在seven_dof_arm_config/config文件夹

```
controller_manager_ns: controller_manager
controller_list:
  - name: seven_dof_arm/seven_dof_arm_joint_controller
    action_ns: follow_joint_trajectory
    type: FollowJointTrajectory
    default: true
    joints:
      - shoulder_pan_joint
      - shoulder_pitch_joint
      - elbow_roll_joint
      - elbow_pitch_joint
      - wrist_roll_joint
      - wrist_pitch_joint
      - gripper_roll_joint
  - name: seven_dof_arm/gripper_controller
    action_ns: follow_joint_trajectory
    type: FollowJointTrajectory
    default: true
    joints:
      - finger_joint1
      - finger_joint2
```





---

```shell
sudo apt-get intall
```

### ros_control

> 二进制 ros-kinetic  源代码 ros_kinetic

二进制

```
sudo apt-get install ros-kinetic-controller-manager
sudo apt-get install ros-kinetic-control
```

源代码

/home/akingse/package_ws/src/ ros_control

/home/akingse/package_ws/src/ ros_controllers

> CMake Error at /opt/ros/kinetic/share/catkin/cmake/catkinConfig.cmake:83 (find_package):
> Could not find a package configuration file provided by "cmake_modules"
> with any of the following names:
>
> cmake_modulesConfig.cmake
> cmake_modules-config.cmake
>
> Add the installation prefix of "cmake_modules" to CMAKE_PREFIX_PATH or set
> "cmake_modules_DIR" to a directory containing one of the above files.  If
> "cmake_modules" provides a separate development package or SDK, be sure it
> has been installed.

```shell
find_package(catkin REQUIRED COMPONENTS
  cmake_modules
  hardware_interface
  pluginlib
  roscpp
)
#缺少所需依赖
sudo apt-get install ros-kinetic-
sudo apt-get install ros-kinetic-cmake-modules
#回车能全装？

manipulation
moveit_ros_plannin
```

> /home/akingse/tempopkg_ws/src/ros_control/transmission_interface/src/transmission_parser.cpp:56:28: error: ‘nullptr’ was not declared in this scope
> TiXmlElement *trans_it = nullptr;

controller编译通过

---

## ros_control

机器人控制中间件，包含一系列控制接口，硬件接口，控制器工具等

*[combined_robot_hw](http://wiki.ros.org/combined_robot_hw?distro=kinetic) | [combined_robot_hw_tests](http://wiki.ros.org/combined_robot_hw_tests?distro=kinetic) | [controller_interface](http://wiki.ros.org/controller_interface?distro=kinetic) | [controller_manager](http://wiki.ros.org/controller_manager?distro=kinetic) | [controller_manager_msgs](http://wiki.ros.org/controller_manager_msgs?distro=kinetic) | [controller_manager_tests](http://wiki.ros.org/controller_manager_tests?distro=kinetic) | [hardware_interface](http://wiki.ros.org/hardware_interface?distro=kinetic) | [joint_limits_interface](http://wiki.ros.org/joint_limits_interface?distro=kinetic) | [realtime_tools](http://wiki.ros.org/realtime_tools?distro=kinetic) | [transmission_interface](http://wiki.ros.org/transmission_interface?distro=kinetic)*

```shell
sudo apt-get install ros-kinetic-ros-control ros-kinetic-ros-controllers

#or

cd CATKIN_ws/src
wstool init
wstool merge https://github.com/ros-controls/ros_control/tree/kinetic-devel/ros_control.rosinstall

https://github.com/ros-controls/ros_control
https://github.com/ros-controls/ros_control/tree/kinetic-devel/ros_control.rosinstall
https://github.com/ros-controls/ros_control/kinetic-devel/ros_control.rosinstall
#安装失败

wstool update
cd ..
rosdep install --from-paths . --ignore-src --rosdistro kinetic -y
catkin_make

```

---

## OMPL 运动规划

运动学 moveit工具集

运动控制 ros_control

硬件控制

物理仿真gazebo

运动规划——轨迹规划

运动规划——路径规划

开源运动规划库（OMPL）是一个包含许多常用运动规划算法（以基于采样的算法，如RRT、PRM为主）的C++库。也是大名鼎鼎的机器人工具集Moveit!所默认采用的运动规划算法库。

> The default motion planners for move_group are configured using OMPL and the MoveIt interface to OMPL by the MoveIt Setup  Assistant. —–[Moveit! Concepts Documentation](https://moveit.ros.org/documentation/concepts/)

通常进行ROS机器人研究时，我们直接使用Moveit!的接口就可以了。但Moveit!是一个同时集成运动学、运动规划、碰撞检测、3D 感知、导航等的庞大工具集，如果我们只需要研究和使用运动规划功能，那么单独使用OMPL也是不错的选择。

[安装使用](https://www.guyuehome.com/6173)





