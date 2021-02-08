

## 学习moveit

moveit!的使用通过为用户提供接口来调用它，包括C++、Python、GUI三种接口。ROS中的`move_group`节点充当整合器，整合多个独立组件，提供ROS风格的Action和service。`move_group`通过ROS topic和action与机器人通讯，获取机器人的位置、节点等状态，获取数据再传递给机器人的控制器。

`move_group`节点获取到节点状态信息或者机器人变换信息时候，会通过控制器的接口去处理这些信息，比如进行坐标转换、规划场景、3D感知。另外，`move_group`的结构比较容易扩展，不仅具有独立的能力如抓放，运动规划，也可扩展自公共类，但实际作为独立的插件运行。moveit!系统结构图如下：

- 一个平台
- 一系列功能包

![请输入图片描述](http://images.ncnynl.com/ros/2016/Overview.0012.jpg)

![image-20201217084550174](https://i.loli.net/2020/12/17/Z1k2XKAf7nlzegH.png)

### 使用步骤

- 模型URDF

- 配置 moveit setup assistant

- 驱动：机器人控制器插件 controller

- 控制：moveit

[CKZZ](https://www.ncnynl.com/category/ros-moveit/)

[CSDN](https://blog.csdn.net/gpeng832/article/details/73917487)

[古月居](https://www.guyuehome.com/2789)

> MOVEit！是目前针对移动操作最先进的软件。
>
> 它结合了运动规划，操纵，三维感知，运动学，控制和导航的最新进展
>
> 它提供了一个易于使用的平台，开发先进的机器人应用程序，评估新的机器人设计和建筑集成的机器人产品
>
> 它广泛应用于工业，商业，研发和其他领域。
>
> MOVEit！是最广泛使用的开源软件的操作



安装movit

```shell
sudo apt-get update #这个命令，会访问源列表里的每个网址，并读取软件列表，然后保存在本地电脑。
sudo apt-get upgrade #这个命令，会把本地已安装的软件，与刚下载的软件列表里对应软件进行对比，如果发现已安装的软件版本太低，就会提示你更新。
sudo apt-get install ros-kinetic-moveit

sudo apt-get install ros-kinetic-moveit-pr2
source /opt/ros/kinetic/setup.bash
```

### 配置助手(Setup Assistant)

```shell
roslaunch moveit_setup_assistant setup_assistant.launch

sudo apt-get install ros-kinetic-controller-manager
#编译ros_controllers 报错
```

---

## 新建配置包

moveit_demo1

![image-20201208200102249](https://i.loli.net/2020/12/08/gEGkqmcIS1iousM.png)

![image-20201208213751777](https://i.loli.net/2020/12/08/1Z7LFDcNtrHGIbk.png)

![image-20201221081349258](https://i.loli.net/2020/12/21/suherjUFAwfqM7G.png)

![image-20201208214439202](https://i.loli.net/2020/12/08/uyoT6Q7FAv4weCK.png)

---

### 重新来过

moveit_demo2

![image-20201221123600713](https://i.loli.net/2020/12/21/5ICQZbwozUPyV9L.png)

![image-20201221123627100](https://i.loli.net/2020/12/21/tNzvMAG6j98kgsB.png)

![image-20210108082239948](https://i.loli.net/2021/01/08/fn8S7mqFsCBRpha.png)

world_joint

world_frame

![image-20201221123728282](https://i.loli.net/2020/12/21/t2g1KJsifpEdBTO.png)

![image-20201221123829291](https://i.loli.net/2020/12/21/fFda3QG2TWMuAKD.png)

Add kin. Chain

base_link

gripper

![image-20201221124001845](https://i.loli.net/2020/12/21/DZwKAfOr85G37NF.png)

![image-20201221124110830](https://i.loli.net/2021/01/07/nlmqkHKI6bAW75d.png)

添加几个标准位姿

init_pose=[0,0,0,0,0,0,0.255,0,0]

home_pose=[0,-pi/6,pi/3,-2*pi/3,-pi/2,0,0.1,pi/2,0]=[0, -0.5236, 1.0472, -2.0944, -1.5708, 0, 0.1, 1.5708, 0]

![image-20210107224058343](https://i.loli.net/2021/01/07/YrhxRBpe4oGWdiu.png)

![image-20201221124255154](https://i.loli.net/2020/12/21/af2EyNPnv34JLe5.png)

![image-20201221124316307](https://i.loli.net/2020/12/21/V6SZiO9UNj7uHTr.png)

![image-20201221131531358](https://i.loli.net/2021/01/07/ibU6PFJwOarEekh.png)

rosrun moveit_demo3 moveit_fk_demo.py命名 moveit_demo3rosrun moveit_demo3 moveit_fk_demo.py

![image-20210107224744299](https://i.loli.net/2021/01/07/xDQbCSf35kHIMPR.png)

---

```
roslaunch moveit_demo3 demo.launch
rosrun moveit_demo3 moveit_fk_demo.py

roslaunch moveit_demo2 demo.launch
roslaunch moveit_demo1 setup_assistant.launch

roslaunch moveit_demo1 gazebo.launch
roslaunch moveit_demo1 demo_gazebo.launch
```

![image-20201221132444877](https://i.loli.net/2020/12/21/vKe2Xa5HpYlTDqj.png)

![image-20201221131806745](https://i.loli.net/2020/12/21/ngdGZONfjJ1Fxmp.png)

TF 坐标系（默认，X红Y绿Z蓝）

![image-20210108100052530](https://i.loli.net/2021/01/08/flWg2tBso3k1a6L.png)

home_pose

![image-20210108210740631](https://i.loli.net/2021/01/08/bTkQJFD3xsBvpLH.png)

![image-20210108215127733](https://i.loli.net/2021/01/08/zpRMdNCBhkUYF46.png)