## Usage

position controller:
Open a first terminal and run:
```
$ ros2 launch iiwa_bringup iiwa.launch.py
```
in a second terminal run:
```
$ ros2 run ros2_kdl_package ros2_kdl_node
```

velocity controller:
Open a first terminal and run:
```
$ ros2 launch iiwa_bringup iiwa.launch.py command_interface:="velocity" robot_controller:="velocity_controller"
```
in a second terminal run:
```
$ ros2 run ros2_kdl_package ros2_kdl_node --ros-args -p cmd_interface:=velocity
```

effort controller:
Open a first terminal and run:
```
$ ros2 launch iiwa_bringup iiwa.launch.py command_interface:="effort" robot_controller:="effort_controller" use_sim:=true
```
In five seconds, press the play button in Gazebo.


in a second terminal run:
```
$ ros2 run ros2_kdl_package ros2_kdl_node --ros-args -p cmd_interface:=effort


```
in this case the robot will be launched with the effort interface in the joint space. To utilize the effort controller in the operational space, you have to comment the line 300 and uncomment the line 303.


To plot the torque on matlab you need to modify the script by inserting the path of the folder containing the bag file.
To generate the bag file:
ros2 bag record -o subset /effort_controller/commands

