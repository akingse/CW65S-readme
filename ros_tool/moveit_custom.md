## my_dofnine

```shell
记录一个路径场景（select start state 示教完毕 update）

test
roslaunch probot_bringup probot_anno_bringup.launch sim:=true
rosrun probot_anno_demo moveit_fk_demo.py

使用gui
joint_state_publisher 

roslaunch moveit_demo2 demo.launch sim:=true
roslaunch moveit_demo2 move_group.launch sim:=true
roslaunch moveit_demo2 moveit_rviz.launch sim:=true #status error:No transform from [Link1] to [base_link]

---
roslaunch probot_anno_moveit_config demo.launch
rosrun probot_anno_demo moveit_fk_demo.py

---
roslaunch moveit_demo2 demo.launch
rosrun moveit_demo2 moveit_fk_demo.py



```

```
关节数据
[-0.13885424, -0.35869032,  1.4412241 ,  0.57511437,  2.1155981 ,-2.97136583,  0.23458294, -2.59168916,  0.28345325],
[-0.13885424, -0.52662008,  2.05098402, -3.00830844, -2.1155981 ,0.17022682,  0.23458294, -2.59168916,  0.28345325],
[-2.87072152,  3.72653349, -2.06579373, -0.40161562,  1.10872726,0.62955839,  0.23458294, -2.59168916,  0.28345325],
[-2.87072152,  3.45812224, -1.42801803,  2.37061259, -1.10872726,-2.51203426,  0.23458294, -2.59168916,  0.28345325]]

[ 0.        , -1.04719755,  2.0943951 , -2.61799388, -1.57079633,        0.        ,  0.1       ,  1.57079633,  0.        ]

更换运动学插件，TRACK_IK或者ikfast

[-2.58923072, -1.2208964 ,  2.46495228, -1.24405196,  1.53816691,-1.57088088,  0.20846856,  1.47592855,  0.03890189],
[-2.58923072, -0.50950044,  2.31827468,  1.33282233, -1.53816691,1.57071177,  0.20846856,  1.47592855,  0.03890189],
[ 1.25612246, -2.63209208, -2.31827428,  1.8087716 ,  1.58205407,1.57078066,  0.20846856,  1.47592855,  0.03890189],
[ 1.25612246, -1.92069604, -2.46495275, -1.89753863, -1.58205407,-1.570812  ,  0.20846856,  1.47592855,  0.03890189]]))

```



---

## 节点信息

```shell
三连
rosnode info /robot_state_publisher #节点
rostopic info /joint_states 
rostopic echo /joint_states

rosnode info /industrial_robot_simulator
 * /joint_states [sensor_msgs/JointState]
 * /robot_status [industrial_msgs/RobotStatus]

rostopic info /joint_path_command
rostopic echo /joint_path_command

rostopic echo /robot_status
```



```
#/joint_states
name: [joint_1, joint_2, joint_3, joint_4, joint_5, joint_6]
position: [0.0009051775042898953, -0.0005550129907205702, 0.0008333646869286896, -0.0008776691919192671, 0.00036969487462192767, 0.000293126606848091]
velocity: []
effort: []

/joint_path_command
positions: [-0.0008462253655306995, -0.0003385693449527025, 5.294424481689904e-06, -0.00044229005556553603, 0.0007309884373098612, -0.0005663525182753801]
    velocities: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
    accelerations: [0.3645209769196936, 0.6272169218038169, 0.3497290685576097, 1.269330644892616e-05, 0.9760929948690851, 0.42220063982185374]

```



### MoveIt编程实现关节空间机械臂运动(逆运动学)

[moveit](https://www.guyuehome.com/17379)

使用的是probot机械臂模型，还是在关节空间下。首先看一下逆运动学规划的例程，逆运动学规划简单的说就是直接给机械臂末端机构需要到达目标的位置，由系统求出逆解之后进行路径规划，从而实现的机械臂运动。

```shell
roslaunch probot_anno_moveit_config demo.launch
rosrun probot_anno_demo moveit_ik_demo.py
#python /home/akingse/catkin_ws/src/PROBOT_Anno/probot_anno_demo/scripts/moveit_ik_demo.py
```

```
四元数表示方式，其模为1
p=cos(Θ/2)+sin(Θ/2)(i,j,k)==w+(x,y,z)

target_pose.pose.position.x = 0.2593
target_pose.pose.position.y = 0.0636
target_pose.pose.position.z = 0.3787
target_pose.pose.orientation.w = 0.8
```

---

## rqt_plot数据流

### 关节轨迹图

```
rqt_graph 
rqt_plot #窗口输入，回车，可查看所有topic
```

我们可以登录Matplotlib官网发现，kinetic中的python2.7和Matplotlib不兼容，并且不再支持Python2。

因此，我们需要寻找另一个可视化工具，PyQtGraph。

```
pip install pyqtgraph

rqt_plot
/joint_states/position[0]
/joint_states/velocity[0]

rosrun rqt_tf_tree rqt_tf_tree 

rqt_plot /joint_states/position[2], /joint_states/position[3], /joint_states/position[4], /joint_states/position[5], /joint_states/position[6], /joint_states/position[8]

rqt_plot /joint_states/velocity[2], /joint_states/velocity[3], /joint_states/velocity[4], /joint_states/velocity[5], /joint_states/velocity[6], /joint_states/velocity[8]
```

![image-20210108223122172](https://i.loli.net/2021/01/08/N34fVhaHCq5P1up.png)





---

## 节点图 rqt_graph

![image-20201220143056368](https://i.loli.net/2021/01/07/zOGUS5ljNhQIWTH.png)

![image-20201220085701449](https://i.loli.net/2021/01/07/zuroJ3MEGmA4HZf.png)

![image-20201221132912755](https://i.loli.net/2021/01/07/86NE2emVgwOnDjl.png)

```
rosnode list
```

> /joint_state_publisher
> /move_group
> /moveit_fk_demo_15561_1608425199302
> /robot_state_publisher
> /rosout
> /rqt_gui_py_node_16841
> /rviz_cw65s_ubuntu_14669_2246375166774708252

```
rostopic list
```

> /attached_collision_object
> /collision_object
> /execute_trajectory/cancel
> /joint_states
> /move_group/cancel
> /move_group/display_contacts
> /move_group/goal
> /move_group/result
> /move_group/status
> /pickup/cancel
> /place/cancel
> /planning_scene
> /rosout
> /rviz_visual_tools_gui
> /statistics
> /tf /tf_static
> /trajectory_execution_event

```
rosservice list
```



```
rosnode info /joint_state_publisher
rosnode info /move_group

rostopic info /joint_states
rosnode info /robot_state_publisher
```

> Type: sensor_msgs/JointState
>
> Publishers: 
>
>  * /joint_state_publisher (http://cw65s-ubuntu:44569/)
>
> Subscribers: 
>
>  * /robot_state_publisher (http://cw65s-ubuntu:40119/)
>  * /move_group (http://cw65s-ubuntu:41669/)

```
rostopic echo /joint_states
```

> name: [joint_1, joint_2, joint_3, joint_4, joint_5, joint_6]
> position: [-0.0006657203105278314, -0.000185268749948591, 0.0007059666900895536, 0.000373943573795259, 0.0009438167749904096, -0.0002092421990819276]
> velocity: []
> effort: []

```
rostopic echo /move_group/fake_controller_joint_states 
```

> name: [joint_1, joint_2, joint_3, joint_4, joint_5, joint_6]
> position: [-0.0006657203105278314, -0.000185268749948591, 0.0007059666900895536, 0.000373943573795259, 0.0009438167749904096, -0.0002092421990819276]
> velocity: []
> effort: []

```
rostopic echo /move_group/display_planned_path
```

> 关节角转动记录

---

显示机器人轨迹

![image-20210107082529001](https://i.loli.net/2021/01/07/lce21VCsRhyPGH5.png)

显示末端轨迹

![image-20210107100052548](https://i.loli.net/2021/01/07/GwyABuJtQeWzxCK.png)





