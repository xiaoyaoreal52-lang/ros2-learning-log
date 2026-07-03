# Gesture-Controlled Simulated Robotic Arm

## Goal

Build a simulated robotic arm that can be controlled by a hand-mounted device.

## Why Start With Simulation

The current budget is limited, so the first version will use simulation instead of a real robotic arm.

This still teaches the important parts:

- ROS 2 communication
- IMU data reading
- Serial communication
- Control mapping
- TF
- URDF
- RViz
- MoveIt 2

## Planned System

```text
Hand device
  -> ESP32
  -> IMU and buttons
  -> serial or wireless data
  -> ROS 2 input node
  -> mapping node
  -> simulated robotic arm
```

## Minimum Hardware List

- ESP32 development board
- MPU6050 or BNO055 IMU
- Several buttons
- Joystick module
- Breadboard and jumper wires
- USB data cable
- Strap or glove

## First Milestone

Use keyboard or command-line input to control a simulated robotic arm.

## Second Milestone

Read IMU data from ESP32 and publish it as a ROS 2 topic.

## Third Milestone

Map hand movement to simulated robotic arm movement.
