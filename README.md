# ROS 2 Learning Log

This repository records my ROS 2 learning journey and the project notes for a gesture-controlled simulated robotic arm.

## Current Environment

- Windows + WSL2
- Ubuntu 24.04 installed on `D:\WSL\Ubuntu-24.04`
- ROS 2 Jazzy
- Workspace: `~/ros2_ws`

## Learning Progress

- ROS 2 installation and WSL setup
- Node, Topic, Message
- Publisher and Subscriber
- Service and custom Python service node
- Parameter
- Launch concept
- TF coordinate transforms
- URDF concept

## Project Goal

Build a simulated robotic arm controlled by a hand-mounted device.

Planned hardware:

- ESP32
- IMU module, such as MPU6050 or BNO055
- Buttons
- Joystick module

Planned software:

- ROS 2 Python nodes
- Serial communication
- URDF robotic arm model
- RViz visualization
- MoveIt 2 control

## Repository Structure

```text
logs/      Daily learning logs
notes/     Concept notes
projects/  Project design and implementation notes
```
