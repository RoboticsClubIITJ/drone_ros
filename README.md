
# drone_ros
This is the tutorial for setting-up a drone in an evironment with all its packages in ROS.

## Prerequisites
- ROS Melodic /Kinetic /Hydro
- Gazebo 8 or higher
- Rviz
- Existing catkin_ws

---

## 1) Setup
### 1.1
### 1.2 Alternative setup 
(Try this only if 1.1 does not work out for you)
- First delete all the residual drone packages that you cloned in 1.1
- Clone all the packages stated below in the src folder in your catkin_ws

```bash

$ cd catkin_ws/src
$ git clone https://github.com/tu-darmstadt-ros-pkg/hector_quadrotor.git
$ git clone https://github.com/tu-darmstadt-ros-pkg/hector_localization.git
$ git clone https://github.com/tu-darmstadt-ros-pkg/hector_models.git
$ git clone https://github.com/tu-darmstadt-ros-pkg/hector_gazebo.git


```
- Compile the catkin_ws to build all the packages


```bash

$ cd catkin_ws
$ catkin_make

```


## 2) Launch environment
For a smooth interface launch only one of these environments at a time
- For outdoor navigation
```bash
$  roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch
```
- For indoor navigation
```bash
$  roslaunch hector_quadrotor_demo indoor_slam_gazebo.launch
```
## 3) Enable motors
This step can be skipped for most systems. But for the few exceptions, you have to manually turn on the motors for the flight simulation.
```bash
$  rosservice call /enable_motors "enable: true"
```

## 4) Launch teleoperation
For navigation of the drone through terminal input, in a separate terminal enter
```bash
$  rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
