# ros工具包



## 网站资源：

ROSwiki官网：http://wiki.ros.org/cn

GitHub      ：https://github.com/

ExBot       ：http://blog.exbot.net/

ROSwiki    ：http://www.roswiki.com/

ROSClub   ：http://www.rosclub.cn/

OSRF      ：http://www.osrfoundation.org/

Robots     ：http://wiki.ros.org/Robots

Sensors    ：http://wiki.ros.org/Sensors

Books      ：http://wiki.ros.org/Books

Courses    ：http://wiki.ros.org/Courses

算法介绍主要有：

mrpt        ：http://www.mrpt.org/

OpenSLAM ：http://openslam.org/

PCL        ：http://pointclouds.org/

OpenCV    ：http://opencv.org/

移动机器人编程工具包(MRPT)是一个广泛的，跨平台的，开源的c++库，旨在帮助机器人研究人员设计和实现(主要)在同步定位和地图(SLAM)，计算机视觉和运动规划(避障)领域的算法。优先级是代码的效率和可重用性。

库包括易于管理3D(6D)几何，概率密度函数(pdf)上的许多预定义变量(点和位姿，地标，地图)，贝叶斯推理(卡尔曼过滤器，粒子过滤器)，图像处理，路径规划和避障，各种地图的3D可视化(点，占用网格，地标，等等。

![image-20201216205358151](https://i.loli.net/2020/12/16/5QRIUZcTiJV83Kt.png)





## 自动搜索安装ROS依赖包

```
The following additional packages will be installed:
  ros-kinetic-ackermann-steering-controller ros-kinetic-cmake-modules
  ros-kinetic-combined-robot-hw ros-kinetic-combined-robot-hw-tests
  ros-kinetic-controller-manager-tests ros-kinetic-diff-drive-controller
  ros-kinetic-force-torque-sensor-controller
  ros-kinetic-gripper-action-controller ros-kinetic-imu-sensor-controller
  ros-kinetic-joint-trajectory-controller ros-kinetic-position-controllers
  ros-kinetic-qt-gui ros-kinetic-rqt-gui ros-kinetic-rqt-gui-py
  ros-kinetic-rqt-joint-trajectory-controller ros-kinetic-velocity-controllers
The following NEW packages will be installed:
  ros-kinetic-ackermann-steering-controller ros-kinetic-cmake-modules
  ros-kinetic-combined-robot-hw ros-kinetic-combined-robot-hw-tests
  ros-kinetic-controller-manager-tests ros-kinetic-diff-drive-controller
  ros-kinetic-force-torque-sensor-controller
  ros-kinetic-gripper-action-controller ros-kinetic-imu-sensor-controller
  ros-kinetic-joint-trajectory-controller ros-kinetic-position-controllers
  ros-kinetic-qt-gui ros-kinetic-ros-control ros-kinetic-ros-controllers
  ros-kinetic-rqt-gui ros-kinetic-rqt-gui-py
  ros-kinetic-rqt-joint-trajectory-controller ros-kinetic-velocity-controllers

```



```
(Reading database ... 371128 files and directories currently installed.)
Reinstall
ros-kinetic-desktop-full (1.3.2-0xenial-20201203-022538+0000) ...
ros-kinetic-perception (1.3.2-0xenial-20201203-020538+0000) ...
ros-kinetic-desktop (1.3.2-0xenial-20201116-175404+0000) ...
ros-kinetic-viz (1.3.2-0xenial-20201116-174743+0000) ...
ros-kinetic-rqt (0.5.0-0xenial-20201103-035801+0000) ...
python-rosinstall-generator (0.1.22-1) ...
ros-kinetic-urdf-tutorial (0.3.0-1xenial-20201103-234947+0000) ...
ros-kinetic-ur5-moveit-config (1.2.7-1xenial-20201104-020516+0000) ...
ros-kinetic-simulators (1.3.2-0xenial-20201116-174715+0000) ...
ros-kinetic-rqt-common-plugins (0.4.8-0xenial-20201116-173616+0000) ...
ros-kinetic-rqt-launch (0.4.8-0xenial-20201103-051736+0000) ...
ros-kinetic-rqt-web (0.4.8-0xenial-20201103-035105+0000) ...
ros-kinetic-ros-controllers (0.13.6-1xenial-20201103-081535+0000) ...
ros-kinetic-ackermann-steering-controller (0.13.6-1xenial-20201103-075642+0000) ...
ros-kinetic-ur-bringup (1.2.7-1xenial-20201103-235746+0000) ...
ros-kinetic-ur-driver (1.2.7-1xenial-20201103-064305+0000) ...
ros-kinetic-common-tutorials (0.1.10-0xenial-20201103-230506+0000) ...
ros-kinetic-turtle-actionlib (0.1.10-0xenial-20201103-044842+0000) ...
ros-kinetic-actionlib-tutorials (0.1.10-0xenial-20201103-044936+0000) ...
ros-kinetic-amcl (1.14.8-1xenial-20201103-060808+0000) ...
ros-kinetic-move-base (1.14.8-1xenial-20201203-024215+0000) ...
ros-kinetic-dwa-local-planner (1.14.8-1xenial-20201203-023305+0000) ...
ros-kinetic-base-local-planner (1.14.8-1xenial-20201203-021943+0000) ...
ros-kinetic-robot (1.3.2-0xenial-20201103-233358+0000) ...
ros-kinetic-diagnostics (1.9.3-0xenial-20201103-070354+0000) ...
ros-kinetic-diagnostic-aggregator (1.9.3-0xenial-20201103-040419+0000) ...
ros-kinetic-image-pipeline (1.12.23-0xenial-20201103-120914+0000) ...
ros-kinetic-camera-calibration (1.12.23-0xenial-20201103-075136+0000) ...
ros-kinetic-uvc-camera (0.2.5-0xenial-20201103-061557+0000) ...
ros-kinetic-usb-cam (0.3.5-0xenial-20201103-061657+0000) ...
ros-kinetic-ur-kinematics (1.2.7-1xenial-20201104-011501+0000) ...
ros-kinetic-moveit (0.9.18-1xenial-20201104-021959+0000) ...
ros-kinetic-moveit-setup-assistant (0.9.18-1xenial-20201104-020631+0000) ...
ros-kinetic-moveit-planners (0.9.18-1xenial-20201104-015159+0000) ...
ros-kinetic-moveit-planners-chomp (0.9.18-1xenial-20201104-014644+0000) ...
ros-kinetic-clear-costmap-recovery (1.14.8-1xenial-20201203-022011+0000) ...
ros-kinetic-robot-model (1.12.11-0xenial-20201103-065558+0000) ...
ros-kinetic-collada-urdf (1.12.13-1xenial-20201103-053242+0000) ...
ros-kinetic-collada-parser (1.12.13-1xenial-20201103-052104+0000) ...
ros-kinetic-ros-control (0.13.5-1xenial-20201103-050327+0000) ...
ros-kinetic-combined-robot-hw-tests (0.13.5-1xenial-20201103-045240+0000) ...
ros-kinetic-combined-robot-hw (0.13.5-1xenial-20201103-041513+0000) ...
ros-kinetic-image-transport-plugins (1.9.5-0xenial-20201103-083929+0000) ...
ros-kinetic-compressed-depth-image-transport (1.9.5-0xenial-20201103-070703+0000) ...
ros-kinetic-compressed-image-transport (1.9.5-0xenial-20201103-070714+0000) ...
ros-kinetic-velocity-controllers (0.13.6-1xenial-20201103-050352+0000) ...
ros-kinetic-joint-trajectory-controller (0.13.6-1xenial-20201103-050230+0000) ...
ros-kinetic-position-controllers (0.13.6-1xenial-20201103-053247+0000) ...
ros-kinetic-joint-state-controller (0.13.6-1xenial-20201103-054447+0000) ...
ros-kinetic-gripper-action-controller (0.13.6-1xenial-20201103-050216+0000) ...
ros-kinetic-gazebo-ros-control (2.5.20-1xenial-20201103-075644+0000) ...
ros-kinetic-controller-manager-tests (0.13.5-1xenial-20201103-044226+0000) ...
ros-kinetic-rotate-recovery (1.14.8-1xenial-20201203-023445+0000) ...
ros-kinetic-navfn (1.14.8-1xenial-20201203-021955+0000) ...
ros-kinetic-depth-image-proc (1.12.23-0xenial-20201103-083722+0000) ...
ros-kinetic-diagnostic-analysis (1.9.3-0xenial-20201103-044311+0000) ...
ros-kinetic-diagnostic-common-diagnostics (1.9.3-0xenial-20201103-063859+0000) ...
ros-kinetic-diff-drive-controller (0.13.6-1xenial-20201103-065253+0000) ...
ros-kinetic-yocs-cmd-vel-mux (0.8.2-0xenial-20201103-045054+0000) ...
ros-kinetic-theora-image-transport (1.9.5-0xenial-20201103-055643+0000) ...
ros-kinetic-dynamixel-controllers (0.4.1-0xenial-20201103-045743+0000) ...
ros-kinetic-dynamixel-driver (0.4.1-0xenial-20201103-032737+0000) ...
ros-kinetic-effort-controllers (0.13.6-1xenial-20201103-050341+0000) ...
ros-kinetic-executive-smach (2.0.1-0xenial-20201103-071443+0000) ...
ros-kinetic-laser-pipeline (1.6.2-0xenial-20201103-074010+0000) ...
ros-kinetic-laser-filters (1.8.5-0xenial-20201103-062228+0000) ...
ros-kinetic-laser-assembler (1.7.4-0xenial-20201103-062208+0000) ...
ros-kinetic-filters (1.7.5-0xenial-20201103-040401+0000) ...
ros-kinetic-force-torque-sensor-controller (0.13.6-1xenial-20201103-042351+0000) ...
ros-kinetic-forward-command-controller (0.13.6-1xenial-20201103-043634+0000) ...
ros-kinetic-gazebo-ros-pkgs (2.5.20-1xenial-20201103-085548+0000) ...
ros-kinetic-gazebo-plugins (2.5.20-1xenial-20201103-074439+0000) ...
ros-kinetic-gazebo-ros (2.5.20-1xenial-20201103-074506+0000) ...
ros-kinetic-moveit-pr2 (0.7.1-0xenial-20201104-013005+0000) ...
ros-kinetic-pr2-moveit-plugins (0.7.1-0xenial-20201104-003851+0000) ...
ros-kinetic-ur5-e-moveit-config (1.2.7-1xenial-20201104-020230+0000) ...
ros-kinetic-ur3-moveit-config (1.2.7-1xenial-20201104-020502+0000) ...
ros-kinetic-geometry (1.11.9-0xenial-20201103-120903+0000) ...
ros-kinetic-geometry-tutorials (0.2.2-0xenial-20201103-071448+0000) ...
ros-kinetic-gmapping (1.3.10-0xenial-20201103-055845+0000) ...
ros-kinetic-hector-mapping (0.3.5-0xenial-20201103-120408+0000) ...
ros-kinetic-image-cb-detector (0.10.14-0xenial-20201103-074213+0000) ...
ros-kinetic-image-common (1.11.13-0xenial-20201103-083050+0000) ...
ros-kinetic-image-overlay-scale-and-compass (0.2.1-0xenial-20201103-064418+0000) ...
ros-kinetic-stereo-image-proc (1.12.23-0xenial-20201103-115106+0000) ...
ros-kinetic-image-proc (1.12.23-0xenial-20201103-074628+0000) ...
ros-kinetic-image-publisher (1.12.23-0xenial-20201103-061340+0000) ...
ros-kinetic-image-recognition (0.0.4-0xenial-20201103-085909+0000) ...
ros-kinetic-image-recognition-rqt (0.0.4-0xenial-20201103-075213+0000) ...
ros-kinetic-image-rotate (1.12.23-0xenial-20201103-055711+0000) ...
ros-kinetic-image-stream (1.0.7-0xenial-20201103-064330+0000) ...
ros-kinetic-ur3-e-moveit-config (1.2.7-1xenial-20201104-020449+0000) ...
ros-kinetic-image-view2 (2.2.11-1xenial-20201203-015851+0000) ...
ros-kinetic-image-view (1.12.23-0xenial-20201103-115054+0000) ...
ros-kinetic-imu-sensor-controller (0.13.6-1xenial-20201103-054418+0000) ...
ros-kinetic-visualization-tutorials (0.10.5-1xenial-20201103-142234+0000) ...
ros-kinetic-interactive-marker-tutorials (0.10.5-1xenial-20201103-061049+0000) ...
ros-kinetic-moveit-ros (0.9.18-1xenial-20201104-020730+0000) ...
ros-kinetic-joint-limits-interface (0.13.5-1xenial-20201103-041558+0000) ...
ros-kinetic-ur10-moveit-config (1.2.7-1xenial-20201104-020430+0000) ...
ros-kinetic-joint-state-publisher-gui (1.12.15-1xenial-20201103-065645+0000) ...
ros-kinetic-joystick-drivers (1.13.0-1xenial-20201103-085815+0000) ...
ros-kinetic-ur10-e-moveit-config (1.2.7-1xenial-20201104-020417+0000) ...
ros-kinetic-librviz-tutorial (0.10.5-1xenial-20201103-094653+0000) ...
ros-kinetic-moveit-commander (0.9.18-1xenial-20201104-014448+0000) ...
ros-kinetic-moveit-plugins (0.9.18-1xenial-20201104-011335+0000) ...
ros-kinetic-moveit-fake-controller-manager (0.9.18-1xenial-20201104-010757+0000) ...
ros-kinetic-pr2-moveit-config (0.7.1-0xenial-20201104-012619+0000) ...
ros-kinetic-moveit-planners-ompl (0.9.18-1xenial-20201104-010536+0000) ...
ros-kinetic-moveit-ros-benchmarks (0.9.18-1xenial-20201104-011049+0000) ...
ros-kinetic-moveit-ros-control-interface (0.9.18-1xenial-20201104-004754+0000) ...
ros-kinetic-nav-core (1.14.8-1xenial-20201203-021215+0000) ...
ros-kinetic-perception-pcl (1.4.4-0xenial-20201203-014302+0000) ...
ros-kinetic-nodelet-tutorial-math (0.1.10-0xenial-20201103-024652+0000) ...
ros-kinetic-openface-ros (0.0.4-0xenial-20201103-075146+0000) ...
ros-kinetic-pluginlib-tutorials (0.1.10-0xenial-20201103-023630+0000) ...
ros-kinetic-polled-camera (1.11.13-0xenial-20201103-060325+0000) ...
ros-kinetic-pr2-description (1.12.4-1xenial-20201103-053715+0000) ...
ros-kinetic-ps3joy (1.13.0-1xenial-20201103-053917+0000) ...
ros-kinetic-rqt-shell (0.4.9-0xenial-20201103-051404+0000) ...
ros-kinetic-rqt-bag-plugins (0.5.0-1xenial-20201116-173135+0000) ...
ros-kinetic-rqt-plot (0.4.8-0xenial-20201103-050839+0000) ...
ros-kinetic-rqt-robot-plugins (0.5.7-0xenial-20201116-174617+0000) ...
ros-kinetic-ros-tutorials (0.7.1-0xenial-20201103-043600+0000) ...
ros-kinetic-rqt-service-caller (0.4.8-0xenial-20201103-051308+0000) ...
ros-kinetic-rosserial (0.7.7-0xenial-20201103-065841+0000) ...
ros-kinetic-rosserial-arduino (0.7.7-0xenial-20201103-064457+0000) ...
ros-kinetic-rosserial-client (0.7.7-0xenial-20201103-063439+0000) ...
ros-kinetic-turtle-tf (0.2.2-0xenial-20201103-055952+0000) ...
ros-kinetic-turtle-tf2 (0.2.2-0xenial-20201103-045928+0000) ...
ros-kinetic-rqt-tf-tree (0.6.0-0xenial-20201103-050007+0000) ...
ros-kinetic-rosweb (1.0.7-0xenial-20201103-044042+0000) ...
ros-kinetic-rosjson (1.0.7-0xenial-20201103-032602+0000) ...
ros-kinetic-wiimote (1.13.0-1xenial-20201103-063556+0000) ...
ros-kinetic-rqt-publisher (0.4.8-0xenial-20201103-051258+0000) ...
ros-kinetic-rqt-srv (0.4.8-0xenial-20201103-052729+0000) ...
ros-kinetic-rqt-moveit (0.5.7-0xenial-20201103-063649+0000) ...
ros-kinetic-rqt-robot-dashboard (0.5.7-0xenial-20201116-174144+0000) ...
ros-kinetic-rospy-tutorials (0.7.1-0xenial-20201103-041051+0000) ...
ros-kinetic-rosserial-python (0.7.7-0xenial-20201103-033818+0000) ...
ros-kinetic-smach-ros (2.0.1-0xenial-20201103-045830+0000) ...
ros-kinetic-rqt-topic (0.4.11-1xenial-20201103-051355+0000) ...
ros-kinetic-rqt-action (0.4.9-0xenial-20201103-052719+0000) ...
ros-kinetic-rqt-reconfigure (0.5.3-1xenial-20201103-051755+0000) ...
ros-kinetic-rqt-dep (0.4.9-0xenial-20201103-051331+0000) ...
ros-kinetic-tensorflow-ros-rqt (0.0.4-0xenial-20201103-081437+0000) ...
ros-kinetic-rqt-top (0.4.8-0xenial-20201103-035054+0000) ...
ros-kinetic-rqt-runtime-monitor (0.5.7-0xenial-20201103-035047+0000) ...
ros-kinetic-rqt-image-view (0.4.16-1xenial-20201103-065452+0000) ...
ros-kinetic-rqt-joint-trajectory-controller (0.13.6-1xenial-20201103-034941+0000) ...
ros-kinetic-rqt-msg (0.4.8-0xenial-20201103-051745+0000) ...
ros-kinetic-rqt-nav-view (0.5.7-0xenial-20201103-063651+0000) ...
ros-kinetic-rqt-pose-view (0.5.8-0xenial-20201103-063713+0000) ...
ros-kinetic-rqt-py-console (0.4.8-0xenial-20201103-035015+0000) ...
ros-kinetic-rqt-robot-steering (0.5.9-0xenial-20201103-051346+0000) ...
ros-kinetic-rqt-rviz (0.5.10-0xenial-20201103-094416+0000) ...
ros-kinetic-rviz-plugin-tutorials (0.10.5-1xenial-20201103-140950+0000) ...
ros-kinetic-rviz-python-tutorial (0.10.5-1xenial-20201103-140956+0000) ...
ros-kinetic-skybiometry-ros (0.0.4-0xenial-20201103-075157+0000) ...
ros-kinetic-slam-karto (0.7.3-0xenial-20201103-055500+0000) ...
ros-kinetic-stage-ros (1.7.5-0xenial-20201103-062104+0000) ...
ros-kinetic-tensorflow-ros (0.0.4-0xenial-20201103-075237+0000) ...
ros-kinetic-tf2-geometry-msgs (0.5.20-0xenial-20201103-050736+0000) ...
ros-kinetic-transmission-interface (0.13.5-1xenial-20201103-041501+0000) ...
ros-kinetic-turtlesim (0.7.1-0xenial-20201103-023141+0000) ...
ros-kinetic-ur-description (1.2.7-1xenial-20201103-234934+0000) ...
ros-kinetic-urdf-geometry-parser (0.1.0-1xenial-20201103-044733+0000) ...
ros-kinetic-ros-base (1.3.2-0xenial-20201103-121012+0000) ...
ros-kinetic-ros-core (1.3.2-0xenial-20201103-120103+0000) ...
ros-kinetic-ros-comm (1.12.17-1xenial-20201103-044923+0000) ...
ros-kinetic-roslisp (1.9.23-1xenial-20201017-200434+0000) ...
ros-kinetic-rqt-gui-cpp (0.5.0-0xenial-20201103-024824+0000) ...
ros-kinetic-qt-gui-cpp (0.3.17-1xenial-20201103-023525+0000) ...
ros-kinetic-bond-core (1.8.3-0xenial-20201103-035612+0000) ...
ros-kinetic-bondpy (1.8.3-0xenial-20201103-032647+0000) ...
ros-kinetic-camera-info-manager (1.11.13-0xenial-20201103-060145+0000) ...
ros-kinetic-control-toolbox (1.17.0-0xenial-20201103-045104+0000) ...
ros-kinetic-controller-manager (0.13.5-1xenial-20201103-042341+0000) ...
ros-kinetic-costmap-2d (1.14.8-1xenial-20201203-013841+0000) ...
ros-kinetic-moveit-simple-controller-manager (0.9.18-1xenial-20201104-003806+0000) ...
ros-kinetic-moveit-ros-visualization (0.9.18-1xenial-20201104-014710+0000) ...
ros-kinetic-ur-e-description (1.2.7-1xenial-20201103-234944+0000) ...
ros-kinetic-rviz (1.12.17-0xenial-20201103-090629+0000) ...
ros-kinetic-moveit-ros-robot-interaction (0.9.18-1xenial-20201104-011059+0000) ...
ros-kinetic-interactive-markers (1.11.5-1xenial-20201103-055445+0000) ...
ros-kinetic-joint-state-publisher (1.12.15-1xenial-20201103-064431+0000) ...
ros-kinetic-robot-state-publisher (1.13.7-1xenial-20201103-232332+0000) ...
ros-kinetic-laser-geometry (1.6.5-1xenial-20201103-061108+0000) ...
ros-kinetic-ros (1.14.6-1xenial-20201017-204036+0000) ...
ros-kinetic-mk (1.14.6-1xenial-20201017-203102+0000) ...
ros-kinetic-moveit-ros-planning-interface (0.9.18-1xenial-20201104-013508+0000) ...
ros-kinetic-moveit-ros-manipulation (0.9.18-1xenial-20201104-012704+0000) ...
ros-kinetic-moveit-ros-warehouse (0.9.18-1xenial-20201104-010308+0000) ...
ros-kinetic-pcl-ros (1.4.4-0xenial-20201203-011510+0000) ...
ros-kinetic-nodelet-core (1.9.14-0xenial-20201103-050305+0000) ...
ros-kinetic-nodelet-topic-tools (1.9.14-0xenial-20201103-045043+0000) ...
ros-kinetic-rqt-robot-monitor (0.5.13-1xenial-20201116-173248+0000) ...
ros-kinetic-qt-gui-py-common (0.3.17-1xenial-20201017-210742+0000) ...
ros-kinetic-realtime-tools (1.11.1-0xenial-20201103-024328+0000) ...
ros-kinetic-rosbash (1.14.6-1xenial-20201017-070912+0000) ...
ros-kinetic-roscreate (1.14.6-1xenial-20201017-190703+0000) ...
ros-kinetic-warehouse-ros (0.9.4-1xenial-20201103-231455+0000) ...
ros-kinetic-rqt-graph (0.4.11-1xenial-20201103-043937+0000) ...
ros-kinetic-rosmake (1.14.6-1xenial-20201017-071148+0000) ...
ros-kinetic-rqt-console (0.4.9-1xenial-20201103-050850+0000) ...
ros-kinetic-rqt-logger-level (0.4.8-0xenial-20201103-044144+0000) ...
ros-kinetic-rqt-bag (0.5.0-1xenial-20201116-172909+0000) ...
ros-kinetic-rqt-gui-py (0.5.0-0xenial-20201103-033828+0000) ...
ros-kinetic-tf2-kdl (0.5.20-0xenial-20201103-231455+0000) ...
ros-kinetic-xacro (1.11.3-0xenial-20201103-043644+0000) ...
ros-kinetic-controller-interface (0.13.5-1xenial-20201103-041525+0000) ...
ros-kinetic-moveit-ros-move-group (0.9.18-1xenial-20201104-011447+0000) ...
ros-kinetic-moveit-kinematics (0.9.18-1xenial-20201104-010801+0000) ...
ros-kinetic-nodelet (1.9.14-0xenial-20201103-024100+0000) ...
ros-kinetic-rqt-py-common (0.5.0-0xenial-20201103-045805+0000) ...
ros-kinetic-rqt-gui (0.5.0-0xenial-20201017-222445+0000) ...
ros-kinetic-moveit-ros-planning (0.9.18-1xenial-20201104-004945+0000) ...
ros-kinetic-chomp-motion-planner (0.9.18-1xenial-20201104-003644+0000) ...
ros-kinetic-dynamic-reconfigure (1.5.50-0xenial-20201103-043947+0000) ...
ros-kinetic-moveit-ros-perception (0.9.18-1xenial-20201104-003756+0000) ...
ros-kinetic-qt-gui (0.3.17-1xenial-20201017-210728+0000) ...
ros-kinetic-tf-conversions (1.11.9-0xenial-20201103-114806+0000) ...
ros-kinetic-moveit-core (0.9.18-1xenial-20201104-002003+0000) ...
ros-kinetic-geometric-shapes (0.5.4-1xenial-20201103-022954+0000) ...
ros-kinetic-image-transport (1.11.13-0xenial-20201103-053940+0000) ...
ros-kinetic-kdl-parser (1.12.11-0xenial-20201103-041256+0000) ...
ros-kinetic-resource-retriever (1.12.6-1xenial-20201103-022413+0000) ...
ros-kinetic-tf (1.11.9-0xenial-20201103-054008+0000) ...
ros-kinetic-tf2-ros (0.5.20-0xenial-20201103-044823+0000) ...
ros-kinetic-tf2-py (0.5.20-0xenial-20201103-034128+0000) ...
ros-kinetic-roswtf (1.12.17-1xenial-20201103-043906+0000) ...
ros-kinetic-rosservice (1.12.17-1xenial-20201103-042841+0000) ...
ros-kinetic-urdf (1.12.12-0xenial-20201103-040423+0000) ...
ros-kinetic-pluginlib (1.11.3-0xenial-20201103-022357+0000) ...
ros-kinetic-actionlib (1.11.16-2xenial-20201103-043745+0000) ...
ros-kinetic-rostest (1.12.17-1xenial-20201103-035944+0000) ...
ros-kinetic-rosmsg (1.12.17-1xenial-20201103-042045+0000) ...
ros-kinetic-rosnode (1.12.17-1xenial-20201103-042808+0000) ...
ros-kinetic-rostopic (1.12.17-1xenial-20201103-042047+0000) ...
ros-kinetic-roslaunch (1.12.17-1xenial-20201103-025528+0000) ...
ros-kinetic-rosbag (1.12.17-1xenial-20201103-041238+0000) ...
ros-kinetic-rosclean (1.14.6-1xenial-20191214-001017+0000) ...
ros-kinetic-rosmaster (1.12.17-1xenial-20201103-022128+0000) ...
ros-kinetic-rosparam (1.12.17-1xenial-20201103-022214+0000) ...
ros-kinetic-rospy (1.12.17-1xenial-20201103-023834+0000) ...
ros-kinetic-rosunit (1.14.6-1xenial-20201017-190712+0000) ...
ros-kinetic-roslib (1.14.6-1xenial-20201017-185445+0000) ...
ros-kinetic-rospack (2.4.5-1xenial-20191214-014035+0000) ...
python-rosdep (0.20.0-1) ...
python-rosdep-modules (0.20.0-1) ...
ros-kinetic-rosgraph (1.12.17-1xenial-20201103-021158+0000) ...
python-rospkg (1.2.9-100) ...

sudo apt-get install ros-kinetic-desktop-full
sudo apt-get install ros-kinetic-urdf
cmake_modules
```

151.101.108.133 raw.githubusercontent.com

sudo apt-get install ros-kinetic-urdf

error: ‘nullptr’ was not declared in this scope

nullptr是C++11引入的关键字，这个编译器没有支持C++11

```
add cmakelists.txt
set(CMAKE_CXX_STANDARD 11)

catkin_make_isolated
```

长按回车，自动安装补全的所有包；