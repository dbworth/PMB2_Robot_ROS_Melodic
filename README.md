# Simulated PMB2 mobile robot

Code to launch a simulated PMB2 mobile robot from PAL Robotics, 
using ROS Melodic and Gazebo 9.

The latest distribution officially supported by PAL Robotics is ROS Kinetic.  
This repo includes various bug fixes and changes to the simulation parameters.  
To see what the changes are you'll need to 'diff' this code against the original.  

## Installation

This assumes you already have ROS Melodic installed on Ubuntu 18.04

Note: the package `pal_multirobot_msgs` comes from `https://github.com/pal-robotics/pal_msgs` but you don't want to compile that entire meta-package because it includes a lot of messages for things we don't need like computer vision and humanoid robots.  

Install the following packages: 
```
sudo apt-get install ros-melodic-imu-sensor-controller ros-melodic-twist-mux
sudo apt-get install ros-melodic-ros-control ros-melodic-gazebo-ros-control ros-melodic-ros-controllers
```

Put all the ROS packages from this repo into a "catkin build" workspace.

Compile your catkin workspace.

## Start the simulation

Launch the robot in Gazebo:  
```
roslaunch pmb2_gazebo pmb2_gazebo.launch public_sim:=true world:=reemc_indoor
```

Move the robot using keyboard:  
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

You can visualize the LiDAR sensor data in RViz.



## Future work

The code in this repo has been modified to use the standard controllers from ROS Control.  
PAL Robotics wrote their own customized version but it won't compile in ROS Melodic:  
```
https://github.com/pal-robotics-forks/ros_controllers      <-- RobotHW class
https://github.com/pal-robotics-forks/gazebo_ros_control   <-- RobotHWSim class
```


.
