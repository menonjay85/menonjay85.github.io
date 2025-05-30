---
title: "Autonomous Navigation with TurtleBot3 Burger (ROS Noetic)"
author_profile: true
toc: true
key: 0
excerpt: "Extended Kalman Filter, Localization, Simulation, C++, ROS Noetic, TurtleBot3, Burger, Ubuntu, RViz, Gazebo"
header:
  teaser: /assets/gifs/slam/navsim.gif
classes: wide
---

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/9k6Bdcs11Ac"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Robot Setup and Configuration

The TurtleBot3 Burger was configured from scratch using manual installation of ROS Noetic on a Raspberry Pi 4. The OpenCR board was flashed with the required firmware, and serial communication between Pi and motor controllers was verified. ROS workspaces were structured to support modular development, and the robot was controlled remotely via SSH from a ROS master laptop.

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/Kr1VZxtbygU"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## SLAM with GMapping

A 2D occupancy grid map was built using the GMapping algorithm. The robot was teleoperated around the environment while LiDAR data from the LDS-01 scanner was used to populate the map in real-time. The ROS <code>slam_gmapping</code> package was launched with appropriate scan and transform settings to ensure high-resolution mapping.

## Localization with AMCL

After the map was generated, the Adaptive Monte Carlo Localization (AMCL) package was used for global and local localization. AMCL used particle filtering with real-time LiDAR scans to continuously estimate the robot’s position on the map. RViz was used to visualize uncertainty ellipses and trajectory paths.

<!-- ![EKF SLAM]({{ site.url }}{{ site.baseurl }}/assets/images/slam-ekf.gif) -->

## Path Planning and Obstacle Avoidance

The ROS <code>move_base</code> node was configured with global and local planners to navigate the environment autonomously. A navigation goal was specified through RViz, and the robot dynamically avoided obstacles using the local costmap generated from real-time sensor input. Parameters such as inflation radius, recovery behaviors, and planner frequencies were tuned for stability and responsiveness.

Before deploying to hardware, all SLAM and navigation functions were tested in a simulated environment using the TurtleBot3 Gazebo world. Custom launch files allowed switching between simulation and real-world modes for consistent testing and deployment.
<!-- ![Landmark detection]({{ site.url }}{{ site.baseurl }}/assets/images/slam-circle.png) -->

## Source code
To be posted. 

## Reference
 - https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/