# 2026-07-03 ROS 2 First Steps

## What I Set Up

- Installed Ubuntu 24.04 in WSL2.
- Put the Ubuntu WSL distribution on the D drive.
- Installed ROS 2 Jazzy Desktop.
- Created a ROS 2 workspace at `~/ros2_ws`.

## What I Practiced

### Talker and Listener

I ran:

```bash
ros2 run demo_nodes_cpp talker
ros2 run demo_nodes_py listener
```

I learned that:

- `talker` is a publisher.
- `listener` is a subscriber.
- They communicate through the `/chatter` topic.
- The message type is `std_msgs/msg/String`.

### Topic Commands

Useful commands:

```bash
ros2 topic list
ros2 topic info /chatter
ros2 topic echo /chatter
ros2 topic pub /chatter std_msgs/msg/String "{data: 'Hello ROS 2'}"
```

Main idea:

```text
Topic = a communication channel.
Publisher sends messages to a topic.
Subscriber receives messages from a topic.
```

### Service

I practiced:

```bash
ros2 run demo_nodes_cpp add_two_ints_server
ros2 service call /add_two_ints example_interfaces/srv/AddTwoInts "{a: 3, b: 5}"
```

I learned:

```text
Service = request once, reply once.
```

### Custom Multiply Service

I created a package:

```bash
ros2 pkg create --build-type ament_python my_math --dependencies rclpy example_interfaces
```

I wrote a Python service node called `multiply_server`.

It receives:

```text
a = 3
b = 5
```

It returns:

```text
sum = 15
```

Even though the field is called `sum`, I used it to store the multiplication result.

### Parameter

I practiced:

```bash
ros2 param list /talker
ros2 param get /talker use_sim_time
ros2 param set /talker use_sim_time true
```

Main idea:

```text
Parameter = runtime configuration for a node.
```

### TF

I practiced static TF:

```bash
ros2 run tf2_ros static_transform_publisher 0.2 0 0.1 0 0 0 base_link laser
ros2 run tf2_ros tf2_echo base_link laser
```

I learned:

```text
TF describes the position and rotation between coordinate frames.
base_link is the robot body frame.
laser is the sensor frame.
```

## Notes

I also saw repeated Fast DDS shared-memory warnings:

```text
RTPS_TRANSPORT_SHM Error
```

For the current beginner exercises, these warnings did not block ROS 2 communication.
