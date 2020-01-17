# mapviz
Mapviz is a ROS-based visualization tool with a plug-in system similar to rviz focused on visualization 2D data. For official ROS wiki page of mapviz, please visit [this](http://wiki.ros.org/mapviz) link.


## Installation
**TESTED PLATFORM:** Ubuntu 16.04 with ROS Kinetic

Although there is an option to install with apt manager, I prefer to install from source.

* Go your catkin workspace and find src directory.
```
$ cd catkin_ws/src
```
* Clone necessary packages
```
$ git clone https://github.com/swri-robotics/mapviz.git --branch $ROS_DISTRO-devel
$ git clone https://github.com/swri-robotics/marti_common.git --branch $ROS_DISTRO-devel
$ git clone https://github.com/swri-robotics/marti_messages.git --branch indigo-devel
```
* Go to root of your workspace and install dependencies
```
$ cd catkin_ws
$ rosdep install --from-paths src --ignore-src
```

#############################################################

**WARNING1:** If you have any error after rosdep install like:
```
Err:3 http:/
/mirrors.tuna.tsinghua.edu.cn/ros/ubuntu xenial/main amd64 ros-kinetic-unique-id amd64 1.0.5-0xenial-20190320-125240-0800
  404  Not Found [IP: 2402:f000:1:408:8100::1 80]
 ```
* Run ```sudo apt update```.

**AT THE END OF WARNING1**

#############################################################


#############################################################

**WARNING2:** If you have error after apt update like:
```
W: GPG error: http://packages.ros.org <YOUR_UBUNTU_VERSION> InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5523BAEEB01FA116
```
* The reason behind this is that the old ROS key has been revoked as part of the measures to deal with a recent security incident with build.ros.org (Security issue on ROS build farm). You need to change it. Here are the steps:
* Delete old key
```
$ sudo apt-key del 421C365BD9FF1F717815A3895523BAEEB01FA116
```
* Add new key
```
$ sudo -E apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
* Now clean the cache and update
```
$ sudo apt clean && sudo apt update
```
* For further info, you can check [this](https://answers.ros.org/question/325039/apt-update-fails-cannot-install-pkgs-key-not-working/) link. 
  
**AT THE END OF WARNING2**

#############################################################


* Now you can build catkin workspace.
```
$ cd catkin_ws
$ catkin_make
```






