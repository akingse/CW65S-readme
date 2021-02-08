## ROS学习——URDF文件解析

[[URDF官方说明文档](http://wiki.ros.org/urdf/XML)]

> 1. sensor/proposals
>    传感器描述，如相机和雷达等
> 2. link
>    描述连杆的运动学参数和动态参数
> 3. transmission
>    描述关节和驱动器之间的转换关系
> 4. joint
>    描述关节的运动学参数和动态参数
> 5. gazebo
>    描述仿真内容，如阻尼和摩擦等
> 6. sensor
>    传感器描述，如相机和雷达等
> 7. model_state
>    描述模型当前状态
> 8. model
>    描述模型运动学参数和动态参数

### [URDF教程](https://blog.csdn.net/dulaiduwangduxing/article/details/45395357)

my_urdf_robot

让我们开始非常简单的创建这个树型结构的描述文件，不用担心维度等的问题。创建一个my_robot.urdf文件，内容如下：

### 添加坐标系和转轴：

base_link(coordinate0，axis0)，link1(coordinate1,axis1)，link2(coordinate2,axis2)，link3(coordinate3,axis3)，gripper(coordinate_gripper)。

末端关节为fixd

![这里写图片描述](https://i.loli.net/2020/12/21/dU7LCyJHFGDuTem.jpg)



---

## [6轴机器臂的URDF文件的生成并用rviz和moveit显示](https://blog.csdn.net/pathfinder1987/article/details/85220321)



2.SolidWorks利用URDF插件，生成机器臂URDF工程文件

3.URDF文件导入rviz中并显示；

4.在moveit中显示URDF文件。

solidwork2014

首先，是设置刚体坐标系/固定坐标系，选择base_link为固定坐标系

添加机器臂模型，添加成功之后如下图所示，此时可通过控制面板对机器臂进行操控，至此rviz上显示自定义机器臂的设置工作已经结束。

```
roscore
rosrun moveit_setup_assistant moveit_setup_assistant
```

### MoveIt！ 7自由度机械手

MoveIt！由ROS中一系列移动操作的功能包组成，包含运动规划，操作控制，3D感知，运动学，碰撞检测等等，而且提供友好的GUI。

步骤详解

1. 加载URDF
   这里有两个选择，一个是新建一个配置功能包，一个是使用已有的配置功能包，我们选择新建，在源码中找到urdf文件。如果已有配置功能包，那么新建后会覆盖原有的文件。

2. Self-Collision
   点击左侧第二项Self-Collision，配置自碰撞矩阵，这里我们选择默认的采样点数量是10000个，按照这个默认值生成碰撞矩阵。

\3. Virtual Joints
如果一个机械手固定在移动机器人上，我们需要定义一个虚拟关节，虚拟关节可以与移动基座关联，这里的机械手是固定不动的，所以可以不需要虚拟关节。
\4. Planning Groups
在这个机械手的计划组中，为达到目标位姿我们需要建立joints、links两个规划组，一个是机械臂部分，一个是夹具部分。

---

## xacro模型文件

常量定义与调用

```
<xacro:property name="math_PI" value="3.14159">
${math_PI}
```

宏定义与调用

```
<xacro:property name="math_PI" value="3.14159">

```

