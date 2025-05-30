---
title: "Kinematic Analysis and Simulation of MyCobot280 M5 using MATLAB and Simscape"
author_profile: true
toc: true
key: 5
excerpt: "Python, MATLAB, PID Control"
header:
  teaser: /assets/gifs/mycobot/mycobot-simscape.gif
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

This project focuses on the modeling, simulation, and control of the MyCobot 280 M5 6-DOF robotic arm using MATLAB and Simscape Multibody. A comprehensive workflow was established that integrates CAD-based physical modeling, kinematic analysis, and real-time actuation through the <code>pymycobot</code> Python library. The objective was to evaluate both virtual and physical performance of the manipulator in a simulated digital twin environment. 

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/id8E9aI6zaU"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Simscape-Based Digital Twin
The simulation environment was constructed by importing a SolidWorks assembly of the MyCobot 280 into Simscape Multibody using the <code>smimport</code> function. Each link and revolute joint was mapped into the Simulink model with corresponding physical parameters. Joint actuation was configured to accept dynamic input for testing various motion profiles. Mechanics Explorer was used to visualize robot movement in real time.
<br>
Simulink architecture included components like <code>Rigid Transform</code>, <code>Revolute Joint</code>, and <code>World Frame</code>, along with driver and signal blocks to control each DOF.

## Forward and Inverse Kinematics
A forward kinematics model was derived using Denavit-Hartenberg parameters to compute the end-effector pose. MATLAB scripts were used for validation. For inverse kinematics, a combination of analytical and numerical approaches was applied to compute joint angles for given trajectories. These calculations were optionally linked to the Simulink model for online motion execution.
<br>
The kinematic chain was also validated using a Python implementation of joint space commands through the <code>pymycobot</code> API, ensuring that simulation outputs align with physical robot behavior.

## Real-World Interface and Control
Using the <code>pymycobot</code> library, a Python script was developed to send joint angle commands to the MyCobot arm via serial communication. Real-time joint angles were logged and visualized, and motion sequences were tested to verify simulation accuracy. This bridged the gap between digital simulation and real hardware experimentation.
<br>
A feedback loop for positional monitoring was also implemented by querying the Cartesian coordinates using <code>get_coords()</code> and comparing with desired setpoints. 
<br>
Comparative tests between Simscape simulations and real-world arm movements were conducted. Pose tracking, joint synchronization, and motion smoothness were evaluated. Errors between simulated and real trajectories were recorded for refinement.

## Source code

## References
- https://www.elephantrobotics.com/en/
- https://www.mathworks.com/help/sm/index.html
