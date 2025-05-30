---
title: "UR5 Palletizing: Dual-Mode Implementation with Teach Pendant and ROS2"
author_profile: true
toc: true
key: 1
excerpt: "Universal Robots, ROS2, MoveIt, OpenCV, Machine Learning"
header:
  teaser: /assets/images/jenga.gif
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

This project presents a dual-mode approach for implementing a palletizing task using a Universal Robots UR5 arm. The robot was tasked with picking die-like cubes from a linear conveyor and placing them onto a pallet in a structured 3x2 grid. The implementation was carried out using two methodologies: (1) direct programming via the UR Teach Pendant interface, and (2) simulation and control via ROS2 and MoveIt. This comparison highlights trade-offs in flexibility, scalability, and integration complexity.

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/fhbBggKSfb4"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>
<br>
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/AFiHTUThE-w"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

The initial implementation was conducted directly on the UR5 hardware using the Teach Pendant’s block-based programming interface. This method leverages Universal Robots’ Polyscope environment, enabling users to develop sequences with drag-and-drop programming blocks and real-time waypoint teaching.

<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/1qIxVEyiJ3E"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Implementation Details
- <b>Palletizing Wizard:</b> The built-in Palletizing Wizard was employed to define the grid pattern. By specifying the first and last positions of a row, the wizard interpolated intermediate positions, streamlining the programming process.
- <b>Waypoint Definition:</b> Waypoints for pick and place positions were taught by physically guiding the robot arm while holding the Freedrive button, allowing for precise positioning without manual coordinate entry.
- <b>Gripper Control:</b> Gripper operations were integrated using I/O commands within the program, ensuring synchronized opening and closing actions during pick-and-place cycles.
- <b>Looping:</b> A simple loop structure was defined to repeat the pick-place cycle for all six cubes.

## ROS2 Implementation

To overcome the limitations of the Teach Pendant approach, the task was re-implemented in a ROS2 simulation environment using Gazebo and MoveIt. This allowed for greater flexibility, scalability, and integration with other systems.

- The MoveIt Task Constructor was employed to define a sequence of stages for picking and placing, including approach, grasp, lift, transport, and release.
- Gripper actions were controlled via ROS2 services.
