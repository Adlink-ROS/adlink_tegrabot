# ADLINK tegraBot
People-tracking robot according to cloth type using AI

## About the project  
The purpose of this pkg is to demonstrate the abilities of ADLINK M200-JT2 computing platform.
* ADLINK M200-JT2 Edge Inference Platform: with NVIDIA® Jetson™ TX2 [[link](https://www.adlinktech.com/Products/Deep_Learning_Accelerator_Platform_and_Server/Inference_Platform/M200-JT2?lang=en)]  
   
* Video  
    https://youtu.be/7Aw_RRJNXXM  
    https://youtu.be/QR2g3am_0OA  

* Slides  
    https://github.com/Adlink-ROS/adlink_tegrabot/blob/master/document/ADLINK_tegraBot.pdf (not available ATM)  

## Dev Team
* Ewing Kang (ewing.kang@adlinktech.com)
* Alan Chen (alan.chen@adlinktech.com)
* Chester Tseng (chester.Tseng@adlinktech.com)
* Bill Wang (bill.wang@adlinktech.com)
* Ryan Chen (ryanjb.chen@adlinktech.com)
  
ADLINK Technology, Inc  
Advanced Robotic Platform Group  

## License
Apache 2.0  
Copyright 2018 ADLINK Technology, Inc.  

# Tutorial
## Prerequisites

### Hardware
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

### ROS
* Navigation  
  Installation: `$ sudo apt-get install ros-kinetic-navigation*`  
  Source: https://github.com/ros-planning/navigation  
  Notice: if "replan" mode of global planner is malfunctioned, please compile whole pkgs from source.  
  Testing: `$ roslaunch spencer_people_tracking_launch tracking_on_bagfile.launch`  

* Turtlebot2  
  Installation: `$ sudo apt-get install ros-kinetic-turtlebot`  
  Source: https://github.com/turtlebot/turtlebot  

### AI tracking
You need these package installed for the tensorflow_object_detector node to work
* CUDA v8.0
* cudnn v6.0
* libuvc
* (training only) protoc 3.3 (notice the version)

There are 4 packages working together that made the people tracking using AI possible. 
```
cd ~/catkin_ws/src

git clone https://github.com/Adlink-ROS/adlink_tegrabot https://github.com/Adlink-ROS/tf_ai_tracker.git https://github.com/Adlink-ROS/tegrabot_description.git https://github.com/Adlink-ROS/tensorflow_object_detector.git 
```
* **adlink_tegrabot**: main launch collection of the tegrabot
* **tegrabot_description**: robot model (urdf) for rviz 
* **tensorflow_object_detector**: TensorFlow classifier
* **tf_ai_tracker**: people tracking controller 

## Running the demo
### Before your first run
* (optional) Mapping & Time Synchronizing  

### Host launch
* ROS: `$ roslaunch adlink_tegrabot NeuronBot_Demo_Host_AIO.launch`
* shell script: `$ ./PATH_TO_WORKSPACE/adlink_tegrabot/autostart/NeuronBot_Demo_Host_AutoStart.sh)
### visualization
rviz file _neuronbot_demo_client.rviz_ is in the [rviz folder](rviz)

## Optional ROS package
* SPENCER  
  Binary: https://github.com/spencer-project/spencer_people_tracking#installation-from-l-cas-package-repository  
  Source: https://github.com/spencer-project/spencer_people_tracking#installation-from-source  
  Notice: Unless you want to use HOG+SVM [CUDA required], we highly recommend binary version.  

* leg_tracker  
  Source: https://github.com/angusleigh/leg_tracker  
  Notice: The kinetic branch only supports OpenCv 3.3 and higher ver.  
  Testing: $ roslaunch leg_tracker demo_stationary_simple_environment.launch  
 
## Training your own model
Please check our [wiki](https://github.com/Adlink-ROS/adlink_tegrabot/wiki) for more information.

# Project status
v1.0
## Known Issues
* 

## Roadmap
- [ ] Multi robot example  
 
