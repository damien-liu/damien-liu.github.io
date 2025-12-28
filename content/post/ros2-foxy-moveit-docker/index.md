---
title: "Setting up ROS2 Foxy and MoveIt 2 with Docker"
date: 2025-12-28
description: "A simple guide to getting a ROS2 Foxy and MoveIt 2 environment running in a container."
image: cover.jpg
categories:
    - Robotics
    - Development
tags:
    - ROS2
    - Docker
    - MoveIt
---

Setting up ROS2 and MoveIt 2 on a local machine usually leads to dependency hell. It's much cleaner to run everything in a Docker container.

I've been using a VNC-enabled image lately. It allows you to access the GUI tools through a browser. Here is my setup.

### Start the Container

I use the `tiryoh/ros2-desktop-vnc:foxy` image. It has a built-in web VNC server running on port 80 (mapped to 6080).

Run this command to start it:

~~~bash
docker run -it -p 6080:80 --shm-size=512m tiryoh/ros2-desktop-vnc:foxy
~~~

*Note: The `--shm-size=512m` flag is important. Without it, Rviz often crashes due to low shared memory.*

### Install MoveIt 2

Once the container is running, go to `localhost:6080` in your browser. Open the terminal inside the VNC desktop and install the MoveIt 2 packages along with the Panda robot config:

~~~bash
sudo apt update && sudo apt install -y \
  ros-foxy-moveit \
  ros-foxy-moveit-resources-panda-moveit-config \
  ros-foxy-ros2-control \
  ros-foxy-ros2-controllers \
  ros-foxy-xacro
~~~

### Run the Demo

To verify everything is working, launch the Panda arm demo. This will open Rviz and load the robot model.

~~~bash
ros2 launch moveit_resources_panda_moveit_config demo.launch.py
~~~

If you see the robot arm and can interact with the motion planning plugin, you are good to go. It’s a straightforward way to get a robotics environment ready without messing up your host OS.