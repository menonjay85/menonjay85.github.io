---
title: "Quadrotor Control"
author_profile: true
toc: true
key: 2
excerpt: "Raspberry Pi, PID control, C++"
header:
  teaser: /assets/images/quadrotor.jpg
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

Designed and built a quadrotor for autonomous flight. Implemented code for IMU, joystick control, PID control, and Vive sensor integration. 

## Video Demo
<iframe
    width="100%"
    height="50px"
    src="https://www.youtube.com/embed/4o0iD1JMODs"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## Inertial Measurement Unit (IMU)
We get data from both the accelerometer and gyro in the IMU. 
1. Calibrated all 3 gyro DOF to counter drift
2. Calibrated pitch and roll
3. Implemented complementary filter to high pass gyro output and low pass accelerometer output so that both the low noise of the gyro and the long term accuracy of the accelerometer can be utilized

## Safety Limits
To prevent the quadrotor from undesired behaviors, we implemented a number of safety measures to stop the program:
1. Any gyro rate >300 degrees/sec
2. Roll angle >45 or <-45
3. Pitch angle >45 or <-45
4. Keyboard timeout

## P Controller
To provide linear feedback, we implemented proportional controller following: 

`Motor PWM = neutral_power +- pitch/roll/yaw_error * P_value`

## I Controller
To counter constant offsets (power difference of motors, shifts in weight, etc.), we implemented integral controller following: 

`I_term += error * I_gain for every time step`

## D Controller
To maintain angular velocity, we implemented derivative controller following: 

`Motor pulse width = neutral_power +- pitch/roll/yaw_velocity * D_value`

## Joystick Control
To incorporate manual control, we implemented support for joystick input that would do the following:
1. Changing roll/pitch angle
2. Increase/reduce thrust
3. Pause/unpause flight
4. Calibrate sensors
5. Kill program
6. Joystick heartbeat detection (for safety)

## Vive Lighthouse
To achieve autonomous flight, we need to know the pose of the quadrotor in 3D space. We added 4 sensors that would take in IR light transmitted from the [Vive Lighthouse](https://www.vive.com/us/accessory/base-station/), which provides 2 sweeps of planar light. We can then get the X, Y, Z, and theta position of the quadrotor for autonomous flight. 

## Source Code
[Github repo](https://github.com/EricYYang2022/CS410-Quad04)

## Group Members
Eric Yang