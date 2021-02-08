## 记录下遇到的bug

```
sudo rosdep init 
rosdep update
```

> ERROR: cannot download default sources list from:
> https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/sources.list.d/20-default.list
> Website may be down.
>
> reading in sources list data from /etc/ros/rosdep/sources.list.d
> ERROR: unable to process source [https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/osx-homebrew.yaml]:
> 	<urlopen error [Errno 111] Connection refused> (https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/osx-homebrew.yaml)
> ERROR: unable to process source [https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/base.yaml]:

```
gedit /etc/ros/rosdep/sources.list.d/20-default.list

sudo chmod 777 /etc
sudo apt-get install ca-certificates 
sudo gedit /etc/hosts
添加 
151.101.76.133 raw.githubusercontent.com

sudo apt-get update

sudo apt-get install python-rosdep 

```

[IP查询](https://site.ip138.com/raw.Githubusercontent.com/)

[quote](https://blog.csdn.net/u013468614/article/details/102917569)

raw.githubusercontent.com

> 日本 东京 151.101.108.133
>
> 日本 大阪 151.101.88.133
>
> 日本 东京 151.101.228.133
>
> 美国 151.101.0.133
>
> 保留地址 0.0.0.0
>
> 中国 香港 151.101.76.133

加锁

> E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
> E: Unable to lock directory /var/lib/apt/lists/

```
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock

sudo killall apt
sudo killall apt-get
sudo killall synaptic

ps -e | grep apt 
```

---

## (ros/catkin)  ××/××.h: No such file or directory

[quote](https://blog.csdn.net/w383117613/article/details/46049273?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.control)

1.　此.h文件是由自定义消息生成的，如robot_msgs/voltage.msg
    则解决方法是cmakeList中添加：

```
add_executable(robot_control_node  src/robot_control.cpp )
add_dependencies(robot_control_node robot_msgs_gencpp)
target_link_libraries(robot_control_node ${catkin_LIBRARIES})
```

依赖

```
cmakeList.txt
find_package(catkin REQUIRED COMPONENTS
  probot_msgs)
add_dependencies(_node probot_msgs_gencpp)

packege.xml
<build_depend>robot_msgs</build_depend>
<exec_depend>robot_msgs</exec_depend>
```

 2. 此.h文件位于本包include内：
 　　　　　　　解决方法是，在包含目录下包含include包：

```
include_directories(
include
${catkin_INCLUDE_DIRS} 
)
```

 　　　　


  3.　此.h文件位于别的包内，如robot_navigation：

```
则在find_package中添加此包名：
find_package(catkin REQUIRED COMPONENTS
roscpp
rospy
std_msgs
robot_navigation
)
其次，请记得在package.xml中添加
<build_depend>robot_navigation</build_depend>
<run_depend>robot_navigation</run_depend>
```

都不行；

串行编译

```
catkin_make --make-args -j1
```

git clone重装，bug解决；

---

### python pip安装模块

python pip install 

ERROR: You must give at least one requirement to install (see "pip help install")

```
sudo pip install numpy
sudo pip install sympy
cd /usr/lib/python2.7/dist-packages
```

ImportError: cannot import name 'multiarray'

sudo update-alternatives --config python

```
sudo python dofmain.py
```



roscore启动失败 python版本指向

```bash
ls -al /usr/bin/python
移除：
sudo rm -rf /usr/bin/python
新建：
sudo ln -s /usr/bin/python2.7 /usr/bin/python


```





