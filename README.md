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
first send second line should be #!/usr/bin/env python3   & import rclpy
import Node class and inherit from that

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

| Feature/Component      | Description    |
|------------------------|----------------|
| ros2 node list        | list of nodes |
| ros2 node info <node name>       | get info |
| ros2 topic list        | list of topics |
| ros2 topic info <topic name>       | get info |
| ros2 topic echo <topic name>       | see output of a publisher |
| ros2 topic hz <topic name> | see frequency of publisher outputs |
| ros2 interface show <Type> | see data structure of input or output for the topic aftergetting the topic info |
| ros2 service list | list of services |
| ros2 service type <service name> | type of service |
| ros2 interface show <name from above> | show data |
| rqt_qrt | show the gragh |
| colcon build| build project |
| colcon build --packages-up-to time_controler  | build a specific package only |
| ros2 run time_controler nmea_subscriber |
| ros2 launch fixposition_driver_ros2 tcp.launch |
| create client. service, publisher, subsriber| different type of constructors |


