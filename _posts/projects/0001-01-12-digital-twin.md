---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "SLAM, Computer Vision, Loop Closure, ROS, Mobile Robotics, LIDAR"

project:
  title: "LIOSAM : Tightly-coupled Lidar Inertial Odometry via Smoothing and Mapping"
  type: "Jekyll"
  url: "https://github.com/menonjay85/LIOSAM"
  logo: "/assets/images/projects/final/liosam.gif"
  tech: "SLAM, Computer Vision, Loop Closure, ROS, Mobile Robotics, LIDAR"
---



<!-- Add some links here to their bios / labs -->
<p>State estimation, localization, and mapping are the essential requirements for an intelligent mobile robot. However, challenges exist in Real-Time 3D Mapping and Localization. Current technologies like LOAM (<a href="https://frc.ri.cmu.edu/~zhangji/publications/RSS_2014.pdf" target="_blank"><u>Lidar Odometry and Mapping in Real-time</u></a>) struggle with loop closure detection.</p>
<br>
<p>LIO-SAM is a state-of-the-art algorithm that integrates LiDAR and IMU data to perform real-time odometry and mapping. It is particularly effective in environments where GPS signals are weak or unavailable, such as indoors or in urban canyons. The algorithm employs factor graph optimization to fuse data from the LiDAR and IMU sensors, ensuring robust and accurate state estimation. LIO-SAM is designed to handle the complexities of dynamic environments and large-scale mapping, making it suitable for various robotic applications, including autonomous vehicles, drones, and mobile robots.
<br>
<br>
This project was implemented in the Spring quarter of 2024 as a Final project for my CSE 598 course (Perception in Robotics) under Professor <a href="https://www.linkedin.com/in/nakul-gopalan-41a19212/" target="_blank"><u>Nakul Gopalan</u></a>.</p> 

<br>

<img class="img80" src="/assets/images/projects/final/liosam.gif" width="1500"> 
<center><h2>Simulation of a Mobile robot with Velodyne Lidar in Gazebo</h2></center>

<br>

### Basic System Flow

<br>

<img class="img80" src="/assets/images/projects/final/flow.png" width="1200"> 

<p></p>

<br>

<p>I had also put up a presentation for you to refer on LIOSAM. You can refer the same <a href="https://drive.google.com/drive/folders/1xFRH7WxEOgO7WQvZsDazcduJGH1s_SA6?usp=sharing" target="_blank"><u>here</u></a>.</p>
<br>


<!-- Throw in peter stone block diagram
![Peter Stone Block Diagram](/assets/images/projects/final/peterstone.png)
<center><h2>Nate Kohl and Peter Stone, “Policy Gradient Reinforcement Learning for Fast Quadrupedal Locomotion”, ICRA, 2004.</h2></center> -->


<!-- Picture of Peter Stone results -->
<!-- ![Online Learning Results](/assets/images/projects/final/stone_results.png) -->
<!-- <img class="img80" src="/assets/images/projects/final/stone_results.png"> 
<center><h2>Results on a per-trial basis, using online policy gradient RL</h2></center>
<br> -->

<!-- ### Creating a Simulation Environment

<p>I created a simulation environment based off of Pybullet, and made it compatible with OpenAI's Gym workflow, a useful framework for reinforcement learning tasks. The robot modeled in simulation, is defined by a URDF with two joints: a revolute and prismatic joint connected together.</p>

<br> -->

<!-- Add a gif here of the robot moving its 'hips' around -->

<!-- <p>Using an AprilTag, I then perform a set of planar sweeps to cover the parameter space for the leg. It results in a lookup table as shown below - each dot represents a combination of motor commands and the inplane displacement of the leg from the origin <code>(0,0)</code>, when the motors are at their neutral location. 
  In the full lookup table, compiled over multiple hours and ~12 complete inplane sweeps covering the parameter space, it's visually apparent that <strong>1.</strong> the HSA properties remain reasonably consistent over time, and <strong>2.</strong> HSA displacement at a given set of motor values is reasonably
  repeatable, regardless of the actuator's strain rate or direction of movement. The resulting dimensions of the lookup table then define the joint limits in the simulation's URDF file.
</p>
<br> -->
<!-- GIF / image of the lookup table -->


<!-- | Animated Lookup Table  | Full Lookup Table |
| ------------- | ------------- |
| <img class="img80" src="/assets/images/projects/final/lut_animation.gif">  | <img class="img80" src="/assets/images/projects/final/interpolate_lut.png">  |
 -->

<br><br>

