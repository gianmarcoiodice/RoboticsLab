## HOMEWORK 1
### Instructions
open a first terminal:
```bash 
	 sudo apt-get upgrade
	 sudo apt-get upgrade
	 sudo apt-get update
	 colcon build
	 source install/local_setup.bash
	 ros2 launch arm_gazebo arm_gazebo.launch.py
```
open a second terminal and run: 
``` bash
ros2 run ros_ign_bridge parameter_bridge /camera@sensor_msgs/msg/Image@gz.msgs.Image
```
in a third terminal run:
```bash
 ros2 launch arm_description display.launch.py
 ```
in another terminal run:
``` bash
 ros2 run rqt_image_view rqt_image_view 
```
select the topic /videocamera
\\
in another terminal run:
```bash
 ros2 run arm_control arm_controller_node
```
it's important to follow the order of the commands. at the end you will be able to
verify that all the requestes are satisfied. 
even if you just want to see the robot in Rviz, you firstly need to launch the arm_gazebo.launch.py
