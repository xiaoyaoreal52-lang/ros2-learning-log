# 2026-07-04 URDF, RViz, and Joint States

## What I Learned Today

Today I moved from basic ROS 2 communication concepts into the first real robotic arm visualization workflow.

## URDF Basics

I learned that URDF is the robot structure description file.

Main concepts:

```text
link  = robot part or rigid body
joint = connection between two links
```

For example:

```text
base_link
  -> joint_1
link_1
  -> joint_2
link_2
```

## Visual Model in RViz

I created a simple robot description package:

```bash
ros2 pkg create my_robot_description
```

I wrote a URDF file:

```text
~/ros2_ws/src/my_robot_description/urdf/simple_robot.urdf
```

I first displayed:

```text
base_link + laser
```

Then I changed it into a simple 2-DOF arm:

```text
blue base_link cylinder
green link_1
yellow link_2
joint_1
joint_2
```

## robot_state_publisher

I learned that `robot_state_publisher` reads the URDF and publishes TF transforms.

Command:

```bash
ros2 run robot_state_publisher robot_state_publisher ~/ros2_ws/src/my_robot_description/urdf/simple_robot.urdf
```

Important idea:

```text
URDF describes the structure.
robot_state_publisher converts the structure and joint states into TF.
```

## RViz Model Display

I opened RViz:

```bash
rviz2
```

Important RViz settings:

```text
Fixed Frame = base_link
Add display = RobotModel
RobotModel Description Source = File
Description File = /home/ros/ros2_ws/src/my_robot_description/urdf/simple_robot.urdf
```

I learned that RViz may show errors if there is no TF or if movable joints do not have joint state data.

## joint_state_publisher_gui

I installed and used:

```bash
sudo apt install ros-jazzy-joint-state-publisher-gui
ros2 run joint_state_publisher_gui joint_state_publisher_gui
```

This gave sliders for:

```text
joint_1
joint_2
```

Dragging the sliders moved the arm in RViz.

## Program-Controlled Joint Motion

I created a Python test publisher:

```text
~/ros2_ws/joint_wave_pub.py
```

It publishes `/joint_states` automatically.

Main idea:

```text
Python node publishes joint angles
  -> robot_state_publisher receives them
  -> TF is updated
  -> RViz shows the arm moving
```

The key code idea:

```python
msg.name = ["joint_1", "joint_2"]
msg.position = [angle_1, angle_2]
```

## Important Lesson

I learned this important rule:

```text
URDF only describes the robot structure.
Movable joints also need /joint_states to tell ROS 2 their current angles.
```

If `/joint_states` is missing, RViz may show errors such as missing TF data.

## Project Connection

This is directly related to the future hand-controlled robotic arm project.

The future control flow will be:

```text
IMU or hand device data
  -> convert to joint angles
  -> publish /joint_states or controller commands
  -> robotic arm moves in RViz or simulation
```
