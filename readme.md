# ADLINK tegraBot
People-tracking robot according to cloth type using AI

## Abstract  
The purpose of this pkg is to demonstrate the abilities of ADLINK M200-JT2 computing platform.
1. M200-JT2:  
   Coupter using NVIDIA's TX2 process chip   
   
[Official Slides] https://github.com/Adlink-ROS/adlink_tegrabot/blob/master/document/ADLINK_tegraBot.pdf  
[Youtube Video] **TBD**  
[Youtube Video] **TBD  
[![TBD](TBD)](TBD)  

## Developers & Team
Ewing Kang
Alan Chen  
Chester Tseng  
Bill Wang  
Erik Boasson  
Ryan Chen  
  
ADLINK Technology, Inc  
Advanced Robotic Platform Group  

## License
Apache 2.0  
Copyright 2018 ADLINK Technology, Inc.  

## Tutorial
### Prerequisites

**Hardware related**  
* Depth camera: Realsense D400 / Astra / Astra Pro  
  Source: [realsense](https://github.com/intel-ros/realsense), [astra ros](https://github.com/orbbec/ros_astra_camera)  
  Binary for Astra: `$ sudo apt-get install ros-kinetic-astra*`  
  Notice:  
    1. About RealSense SDK 2.0, we highly recommed binary version.
    2. Remember to create udev. If possible, please buy Astra instead of Astra Pro!
  Testing: `$ roslaunch realsense2_camera demo_pointcloud.launch`  

* YDLidar   
  Source: https://github.com/EAIBOT/ydlidar  
  Notice: Remember to laod udev. Could be replaced by any type of lidar.  
  Testing: `$ roslaunch ydlidar x4.launch`  

* Navigation  
  Installation: `$ sudo apt-get install ros-kinetic-navigation*`  
  Source: https://github.com/ros-planning/navigation  
  Notice: if "replan" mode of global planner is malfunctioned, please compile whole pkgs from source.  
  Testing: `$ roslaunch spencer_people_tracking_launch tracking_on_bagfile.launch`  

* Turtlebot2  
  Installation: `$ sudo apt-get install ros-kinetic-turtlebot`  
  Source: https://github.com/turtlebot/turtlebot  

**AI tracking**
There are 4 package working together that made the people tracking using AI possible. 
```
git clone TBD, git clone TBD, git clone TBD, git clone TBD
```
* adlink_tegrabot 
* tegrabot_description 
* tensorflow_object_detector 
* tf_ai_tracker 


**Optional**
* SPENCER  
  Binary: https://github.com/spencer-project/spencer_people_tracking#installation-from-l-cas-package-repository  
  Source: https://github.com/spencer-project/spencer_people_tracking#installation-from-source  
  Notice: Unless you want to use HOG+SVM [CUDA required], we highly recommend binary version.  

* leg_tracker  
  Source: https://github.com/angusleigh/leg_tracker  
  Notice: The kinetic branch only supports OpenCv 3.3 and higher ver.  
  Testing: $ roslaunch leg_tracker demo_stationary_simple_environment.launch  
  <br />


### Setup Steps
* Mapping & Time Synchronizing  
* Host robot
  $ roslaunch adlink_tegrabot NeuronBot_Demo_Host_AIO.launch  
  OR (script)  
  $ ./PATH_TO_WORKSPACE/adlink_tegrabot/autostart/NeuronBot_Demo_Host_AutoStart.sh  

### Known Issues
* 

### Roadmap
- [ ] Multi robot example  
 
