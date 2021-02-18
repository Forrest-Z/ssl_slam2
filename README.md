# SSL_SLAM2
## Lightweight 3-D Localization and Mapping for Solid-State LiDAR (Intel Realsense L515 as an example)

This code is an implementation of paper "Lightweight 3-D Localization and Mapping for Solid-State LiDAR", accepted in IEEE Robotics and Automation Letters, 2021

A summary video demo can be found at [Video](https://youtu.be/Uy_2MKwUDN8) 

**Modifier:** [Wang Han](http://wanghan.pro), Nanyang Technological University, Singapore

Running speed: 20 Hz on Intel NUC, 30 Hz on PC

## 1. Solid-State Lidar Sensor Example
### 1.1 Scene reconstruction example
<p align='center'>
<a href="https://youtu.be/D2xt_5xm_Ew">
<img width="65%" src="/img/mapping.gif"/>
</a>
</p>

### 1.2 Localization with built map 
<p align='center'>
<a href="https://youtu.be/D2xt_5xm_Ew">
<img width="65%" src="/img/localization.gif"/>
</a>
</p>

### 1.3 Comparison
<p align='center'>
<a href="https://youtu.be/D2xt_5xm_Ew">
<img width="65%" src="/img/comparison.gif"/>
</a>
</p>

## 2. Prerequisites
### 2.1 **Ubuntu** and **ROS**
Ubuntu 64-bit 18.04.

ROS Melodic. [ROS Installation](http://wiki.ros.org/ROS/Installation)

### 2.2. **Ceres Solver**
Follow [Ceres Installation](http://ceres-solver.org/installation.html).

### 2.3. **PCL**
Follow [PCL Installation](http://www.pointclouds.org/downloads/linux.html).

Tested with 1.8.1

### 2.4 **OctoMap**
Follow [OctoMap Installation](http://wiki.ros.org/octomap).

```bash
$ sudo apt install ros-melodic-octomap*
```

### 2.5. **Trajectory visualization**
For visualization purpose, this package uses hector trajectory sever, you may install the package by 
```
sudo apt-get install ros-melodic-hector-trajectory-server
```
Alternatively, you may remove the hector trajectory server node if trajectory visualization is not needed

## 3. Build 
### 3.1 Clone repository:
```
    cd ~/catkin_ws/src
    git clone https://github.com/wh200720041/ssl_slam2.git
    cd ..
    catkin_make
    source ~/catkin_ws/devel/setup.bash
```

### 3.2 Download test rosbag
You may download our [recorded data](https://drive.google.com/file/d/1ZY6Kp5MEGBRoSP6cU2YjNTg5qsy8wNIe/view?usp=sharing) if you dont have realsense L515, and by defult the file should be under home/user/Downloads

### 3.3 Launch ROS
if you would like to create the map at the same time, you can run 
```
    roslaunch ssl_slam2 ssl_slam2_mapping.launch
```
or create probability map 
```
    roslaunch ssl_slam2 ssl_slam2_octo_mapping.launch
```

if only localization is required, you may refer to run
```
    roslaunch ssl_slam2 ssl_slam2.launch
```

## 4. Sensor Setup
If you have new Realsense L515 sensor, you may follow the below setup instructions


### 4.1 L515
<p align='center'>
<img width="35%" src="/img/realsense_L515.jpg"/>
</p>

### 4.2 Librealsense
Follow [Librealsense Installation](https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md)

### 4.3 Realsense_ros
Copy [realsense_ros](https://github.com/IntelRealSense/realsense-ros) package to your catkin folder
```
    cd ~/catkin_ws/src
    git clone https://github.com/IntelRealSense/realsense-ros.git
    cd ..
    catkin_make
```

### 4.4 Launch ROS
```
    roslaunch ssl_slam2 ssl_slam2_L515.launch
```

This runs `ssl_slam2_mapping.launch` with live L515 data.

## 5. Citation
If you use this work for your research, you may want to cite
```
@article{wang2021lightweight,
  title={Lightweight 3-D Localization and Mapping for Solid-State LiDAR},
  author={Wang, Han and Wang, Chen and Xie, Lihua},
  journal={arXiv preprint arXiv:2102.03800},
  year={2021}
}
```