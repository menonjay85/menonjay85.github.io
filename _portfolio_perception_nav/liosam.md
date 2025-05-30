---
title: "LIOSAM : Tightly-coupled Lidar Inertial Odometry via Smoothing and Mapping"
author_profile: true
toc: true
key: 8
excerpt: "SLAM, Computer Vision, Loop Closure, ROS, Mobile Robotics, LIDAR"
header:
  teaser: /assets/gifs/liosam.gif
classes: wide
---

{% comment %} 
sidebar:
  - title: "Role"
    image: http://placehold.it/350x250
    image_alt: "logo"
    text: "Designer, Front-End Developer"
  - title: "Responsibilities"
    text: "Reuters try PR stupid commenters should isn't a business model"
{% endcomment %} 

![liosam]({{ site.url }}{{ site.baseurl }}/assets/gifs/liosam.gif)

## Description
State estimation, localization, and mapping are the essential requirements for an intelligent mobile robot. However, challenges exist in Real-Time 3D Mapping and Localization. Current technologies like LOAM ([Lidar Odometry and Mapping in Real-time](https://frc.ri.cmu.edu/~zhangji/publications/RSS_2014.pdf)) struggle with loop closure detection.<br><br>

LIO-SAM is a state-of-the-art algorithm that integrates LiDAR and IMU data to perform real-time odometry and mapping. It is particularly effective in environments where GPS signals are weak or unavailable, such as indoors or in urban canyons. The algorithm employs factor graph optimization to fuse data from the LiDAR and IMU sensors, ensuring robust and accurate state estimation. LIO-SAM is designed to handle the complexities of dynamic environments and large-scale mapping, making it suitable for various robotic applications, including autonomous vehicles, drones, and mobile robots.<br><br>

This project was implemented in the Spring quarter of 2024 as a Final project for my CSE 598 course (Perception in Robotics) under Professor [Nakul Gopalan](https://www.linkedin.com/in/nakul-gopalan-41a19212/).

## Architecture
![liosam-architecture]({{ site.url }}{{ site.baseurl }}/assets/images/liosam-flow.png)
<br>I had also put up a presentation for you to refer on LIOSAM. You can refer the same [here](https://docs.google.com/presentation/d/1CJVPXP0JBlhkUzn0AiCHb0nr4TPdCGXgMYWDUUHfBvU/edit?usp=sharing).

## Source Code


## References
- [Lidar Odometry and Mapping in Real-time](https://frc.ri.cmu.edu/~zhangji/publications/RSS_2014.pdf)