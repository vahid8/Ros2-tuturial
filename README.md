# Ros2-tuturial
## Installation
1- Install ROS2-Humble & colcon(to build the packages)
2- Add it to enviromental variables

```
gedit ~/.bashrc
source /opt/ros/humble/setup.bash
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash
```
test it using 3 terminals

```
ros2 run demo_nodes_cpp talker
ros2 run demo_nodes_cpp listener
rqt_graph
```

## creating working space and add it ot enviromental variables
```
mkdir ros2_ws
cd ros2_ws
mkdir src
colcon build # it will craete all necessary files and folders including setup.bash so you can run it using 
source ~/dev/ros2_ws/install/setup.bash
```

## create ROS2 python package
```
cd src
ros2 pkg create my_robot_controler --build-type ament_python  (youc n also use ament_cmake)  --dependencies rclpy
cd ..
colcon build
```

## add code to your package and run it 
```
cd my_robot_controler/my_robot_controler
touch my_first_node.py
chmod +x my_first_node.py
```
#write your code inside my_first_node (check the example in this repo)
# first send second line should be #!/usr/bin/env python3   & import rclpy
# import Node class and inherit from that

run the code itself using ./myfirstnode
To be able to run it on your ros2 run you need to add it to setup.py in section"entry_points" e.g
sudo vim src/my_robotcontroler/setup.py
entry_points={'console_scripts': ["test_node= my_robot_controler.my_first_node:main"],}
```
cd ~/dev/ros2_ws
colcon build
source ~./bashrc
ros2 run my_robot_controler test_node
```
if you dont want to type "colcon build" each time you make changes to your code you can type "colcon build --symlink-install" once

## command list 
ros2 node list
ros2 node info /first_node
