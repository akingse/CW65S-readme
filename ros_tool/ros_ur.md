## ROS上的UR5机械臂仿真

[UR5](https://www.guyuehome.com/19083)

package位置：/home/akingse/catkin_ws/src/universal_robot

```shell
    cd catkin_ws/src
    git clone -b kinetic-devel https://github.com/ros-industrial/universal_robot.git
    //若版本为kinetic，应将上面命令中的indigo改为kinetic
    cd ..
    rosdep update
    rosdep install --from-paths src --ignore-src --rosdistro kinetic
    catkin_make
    source ~/catkin_ws/devel/setup.bash

```

有的说要连接真实的机械臂的话，需要将下载的包中的ur_driver替换为ur_modern_driver

![https://www.guyuehome.com/wp-content/themes/gyh/editor-md/examples/uploads/20201201_28845.png](https://i.loli.net/2020/12/18/2fQ3evjF5mlrhBA.png)

启动launch

```sh
roslaunch ur_gazebo ur5.launch
#新terminal
roslaunch ur5_moveit_config ur5_moveit_planning_execution.launch sim:=true
#新terminal
roslaunch ur5_moveit_config moveit_rviz.launch config:=true
```

**运动规划** 

在rviz中拖动机械臂改变机械臂的位置，然后点击plan就可以轨迹规划，再点击execute,机械臂就可以运动到目标位置，并且gazebo噶泽波中可以观察到仿真结果。

UR竟然在代码中公开了运动学算法源代码，然而我看不懂（ur_kinematics）

```
roslaunch ur_description view_ur3.launch
```

![image-20201218163646325](https://i.loli.net/2020/12/18/kAuveDolpUmtFCV.png)

RViz版

```
roslaunch ur_description view_ur5.launch

#launch文件中，arg sim默认为false
roslaunch ur5_moveit_config ur5_moveit_planning_execution.launch sim:=true
roslaunch ur5_moveit_config moveit_rviz.launch config:=true
```



```
rqt_graph 
rostopic echo /joint_states #无数据

rosnode list
rostopic list
rosaction list
rosservise list
```



![image-20201218224034281](https://i.loli.net/2020/12/18/R67CtcpYrMAVxim.png)

---


