---
title: "Mario Motorcycle"
author_profile: true
toc: true
key: 3
excerpt: "C, PCB design, CAD, Motor Control, CV"
header:
  teaser: /assets/images/mario-luigi.png
classes: wide
---

Inspired by Mario's motorcycle style from the beloved Mario Kart game, I took on the task of designing, building, and programming a line-following motorcycle of my own. The project made use of a Raspberry Pi Pico W to interpret images captured by a camera and identify the center of a line. Steering control was implemented through a servo, which was governed by a PIC microcontroller, and two additional drive motors facilitated forward motion. 

![mario-motorcycle]({{ site.url }}{{ site.baseurl }}/assets/images/mario-single.jpg)

## Main Components
 - PIC32MX170F256B
 - Raspberry Pi Pico W
 - Adafruit CP2102 Friend
 - ST7735 1.8" 128x160 TFT LCD
 - OV7670 640x480 Camera
 - DRV8835 Dual Low-Voltage H-Bridge

## PCB design
I further enhanced the project by designing three custom Printed Circuit Boards (PCBs) using KiCad:

![PCB]({{ site.url }}{{ site.baseurl }}/assets/images/mario-pcb.png)

## Recognition

The effort was well rewarded during the 2023 Northwestern Tech Cup, where the Mario Motorcycle was recognized with the "Best Design" award. In a tongue-in-cheek nod to the perennial runner-up, the Luigi counterpart to my creation won the "Luigi is Always Second" award. 

![mario-brothers]({{ site.url }}{{ site.baseurl }}/assets/images/mario-brothers.jpg)

