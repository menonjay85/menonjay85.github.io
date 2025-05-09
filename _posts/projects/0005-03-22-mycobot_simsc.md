---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "MATLAB, Robotics, Kinematics, Elephant Robotics"

project:
  title: "Kinematic Analysis and Simulation of MyCobot280 M5 using MATLAB and Simscape"
  type: "Jekyll"
  url: 
  logo: "/assets/snap.png"
  tech: "Python, MATLAB, PID Control"

youtubeId: TpbLKVcOYL4
---

{% include youtubePlayer.html id=page.youtubeId %}

This is an implementation of Extended Kalman Filter (EKF) SLAM from scratch, in C++. The SLAM pipeline is implemented as a series of ROS packages, and can be simulated in Rviz as well as run on a Turtlebot3, using the onboard LiDAR. <br><br>

This project implements the differential drive forward and inverse kinematics that allow the turtlebot to move. Visualization for simulation was done in Rviz, which contains a world with cylindrical obstacles for the turtlebot to detect. All parameters that govern the obstacles and the robot can be edited as ROS parameters. <br><br>

The SLAM pipeline begins by clustering LiDAR distance data by distance. The points in the clusters are then fit to a circle, in order to find the cylindrical obstacles in the scene. The algorithm that performs this is a form of <a href="https://projecteuclid.org/journals/electronic-journal-of-statistics/volume-3/issue-none/Error-analysis-for-circle-fitting-algorithms/10.1214/09-EJS419.full" target="_blank"><u>Gaussian process regression</u></a> which finds the best fitting circle for the cluster. The location and radius of the circle are then used to classify it appropriately into an "obstacle" or "not obstacle" class. <br><br>

Data association then performed, using the mahalanobis distance from previously discovered obstacles to determine if the measurement should be associated with a previous item in the Kalman Filter, or if it should be considered as a new measurement. Finally, the Extended Kalman Filter uses the turtlebot velocity to predict the future state, and then update the Kalman gains, covariance matrix, and state vector accordingly. <br><br>

When noise is added to LiDAR data wheel velocity, and wheel slip is considered, the EKF SLAM algorithm maintains a better estimate of the robot's state than odometry alone. In the video above, the green robot represents the SLAM's estimate, the blue the odometry, and the red the actual position.<br><br>

More information and source code can be found on the project's <a href="https://github.com/javtges/turtlebot-ekf-slam" target="_blank"><u>GitHub repository</u></a>.

<br><br>

