
# Map My World

 The goal of this project is to create a 2D occupancy grid and 3D octomap from a 
 simulated environment using the robot from [Go-Chase-it](https://github.com/Uamarnat/Go-Chase-it)
 with the RTAB-Map package.



## Description

The RTAB-Map (Real-Time Appearance-Based Mapping) is a global loop closure based
SLAM algorithm which recognizes a previously visited location and updates accordingly. 
This package is used to generate a 3D point clouds of the environment and to create
a 2D occupancy grid map for navigation.
## Build
Project was built and executed in Lubuntu Linux with CMake & g++/gcc, ROS and Gazebo installed.

Packages used are the [rtabmap_ros](http://wiki.ros.org/rtabmap_ros) and the [ros-teleop](https://github.com/ros-teleop/teleop_twist_keyboard)

Open the terminal and create the catkin_ws/src workspace and add the files

Build with catkin
```
catkin_make
source devel/setup.bash
```

Launch the world in Gazebo:
```
roslaunch my_robot world.launch
```

In a new terminal tab run the teleop node for keyboard control:
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

In a new terminal tab launch the mapping node:
```
roslaunch my_robot mapping.launch
```

Now you can navigate the robot in the enviornment to create a map. The Rviz
window shows the robot POV and shows the map being built in real time.
Once the map looks reasonable, terminate the mapping node and the rtabmap.db file will be generated 
in the /root/.ros/ folder.

Open another terminal and view the rtabmap.db file using rtabmap-databaseViewer
```
rtabmap-databaseViewer ~/.ros/rtabmap.db
```
## Result
Enviornment created in Gazebo:
![Gazebo map](https://github.com/Uamarnat/Map-My-World/blob/main/screenshots/SS1.png?raw=true)

3D map generated with rtabmap_ros:
![3dmap](https://github.com/Uamarnat/Map-My-World/blob/main/screenshots/SS2.png?raw=true)

Graph view of the map indicating 2 loop closures:
![graph](https://github.com/Uamarnat/Map-My-World/blob/main/screenshots/SS3.png?raw=true)

2D occupancy grid:
![2d occupancy grid](https://github.com/Uamarnat/Map-My-World/blob/main/screenshots/SS4.png?raw=true)

