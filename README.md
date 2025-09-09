# Robotics Lab – Homeworks Collection

This repository contains all the **Robotics Lab** homeworks, organized in separate folders by number.  
Each homework covers different aspects of robotics using **ROS 2**, **Gazebo**, **KDL**, and computer vision.

## Repository Structure
- `1-Homework-main/` – Introduction to robot control (position, velocity, effort).
- `Homework2-main/` – Inverse kinematics with KDL.
- `Homework3-main/` – Vision-based control (Blob detection, ArUco, etc.).
- `Homework4-main/` – Mobile robot navigation with static TFs, SLAM, waypoints, and ARUCO markers.

---

## Homework 1 – Basic Robot Control  
**Goal:** Launch the robot in Gazebo and control it in position, velocity, or effort mode.

**Main commands:**

**Position controller**
```bash
ros2 launch iiwa_bringup iiwa.launch.py
ros2 run ros2_kdl_package ros2_kdl_node
```

**Velocity controller**
```bash
ros2 launch iiwa_bringup iiwa.launch.py command_interface:="velocity" robot_controller:="velocity_controller"
ros2 run ros2_kdl_package ros2_kdl_node --ros-args -p cmd_interface:=velocity
```

**Effort controller**
```bash
ros2 launch iiwa_bringup iiwa.launch.py command_interface:="effort" robot_controller:="effort_controller" use_sim:=true
ros2 run ros2_kdl_package ros2_kdl_node --ros-args -p cmd_interface:=effort
```

---

## Homework 2 – Inverse Kinematics with KDL  
**Goal:** Implement and test inverse kinematics using ROS 2 KDL.  
See the `Homework2-main/` folder for full instructions.

---

## Homework 3 – Vision-Based Control  
**Goal:** Use visual inputs to control the robot. Includes:
- Blob detection
- ArUco marker recognition
- Vision-based trajectory control

**Example: ArUco + Positioning Control**
```bash
ros2 launch iiwa_bringup iiwa.launch.py command_interface:="velocity" robot_controller:="velocity_controller" use_sim:=true use_vision:=true
ros2 launch aruco_ros single.launch.py marker_size:=0.1 marker_id:=201
ros2 run ros2_kdl_package ros2_kdl_vision_control --ros-args -p cmd_interface:=velocity --ros-args -p task:=positioning
```

---

## Homework 4 – Mobile Robot & Navigation  
**Goal:** Implement autonomous navigation for a mobile robot using ROS 2. Includes:
- Building a Gazebo world
- Waypoint navigation
- SLAM and map saving
- ARUCO-based navigation

**Example: Launch the robot and map the environment**
```bash
ros2 launch rl_fra2mo_description gazebo_fra2mo.launch.py
ros2 launch rl_fra2mo_description fra2mo_explore.launch.py
ros2 run rl_fra2mo_description follow_waypoints.py
```

**Save map**
```bash
ros2 run nav2_map_server map_saver_cli -f map
```

---

## Requirements
- ROS 2 (Foxy/Humble depending on implementation)
- Gazebo
- ROS 2 packages: `iiwa_bringup`, `ros2_kdl_package`, `aruco_ros`, `rl_fra2mo_description`

---

## Notes
- Each homework folder contains its own `README.md` with detailed instructions.
- Ensure all dependencies are installed before running the launch files.
