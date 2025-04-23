---
layout: project
permalink: /:title/
category: projects

meta:
  keywords: "Bio-inspired Robotics, Worm Robot, Digital Twin, Geometric Algebra, Koopman Control, Isaac Sim, PID, SMC, Robotics Thesis"

project:
  title: "Bio-Inspired Worm Robot: Dynamics, Control & Digital Twin"
  type: "Jekyll"
  url: "https://github.com/menonjay85/LIOSAM"
  logo: ""
  tech: "Geometric Algebra, Koopman Operator, Fractional PID, Isaac Sim, Digital Twin, LX-16A Servos, NVIDIA Omniverse"
---

<p>My Master's thesis focuses on the design and control of a <strong>5-DOF bio-inspired worm robot</strong> that mimics inchworm-like locomotion through metachronal gait patterns. Inspired by real-world biological strategies such as those seen in caterpillars and centipedes, the project integrates advanced modeling, control, and simulation techniques to achieve realistic movement across uneven terrains and confined environments.</p>

<br>

<img class="img80" src="/assets/images/projects/final/worm_robot.gif" width="1300">
<center><h2>Simulated Worm Robot using NVIDIA Isaac Sim</h2></center>

<br>

### 📌 Objectives
- Design a modular, scalable worm-inspired robot using LX-16A servos.
- Develop forward and inverse kinematics models using **Geometric Algebra** and **Screw Theory**.
- Implement and compare various controllers: **PD**, **PID**, **Fractional PID**, **Sliding Mode**, and **Koopman-based PID**.
- Validate control strategies via both **simulation (Isaac Sim)** and real hardware.
- Develop a **Digital Twin** that synchronizes physical and simulated models for real-time testing.

<br>

### 🔍 Technical Highlights

#### ✅ Kinematics & Dynamics
- Forward kinematics via **rotor algebra** and **dual quaternion representations**.
- Inverse kinematics derived for metachronal gaits, validated in Isaac Sim.
- Full **Euler-Lagrange** formulation and dynamic modeling for 5-DOF system.
- Introduced **Clifford algebra-based Newton-Euler method** for line-based joint torque computation.

#### ✅ Controller Design
- **PD / PID**: Classical baseline controllers.
- **Fractional PID**: Added tuning flexibility for nonlinear dynamics.
- **Sliding Mode Control (SMC)**: Robust control in uncertain terrain.
- **Koopman Operator-based Control**: Linearizes nonlinear dynamics via learned embeddings.

#### ✅ Digital Twin Integration
- Sim-to-real bridge built using Isaac Sim, BusLinker, and LX-16A servo daisy chaining.
- Continuous feedback loop enabled real-time position updates, controller tuning, and sensor data streaming.
- Integrated **ultrasonic range sensor** for azimuth & zenith detection.

<br>

### 🎓 Research Contributions
- First implementation of Koopman + Fractional PID hybrid for worm robots.
- Comparative analysis of controller stability and trajectory tracking.
- Isaac Sim implementation with photorealistic validation for robotics education and experimentation.
- Under review/published in ASME and IEEE journals.

<br>

### 📚 Publications
- **ASME Dynamic Systems and Control Letters** (Under Review)  
- **Robotica** (Accepted)  
- **ASME Translational Robotics** (Revised)  
- **IEEE RA-L & TASE** (In preparation)

<br>

### 📂 Try It or Learn More
- 🔗 <a href="https://github.com/menonjay85/worm-robot-digital-twin" target="_blank"><strong>Code Repository</strong></a>  
- 🖼 <a href="https://drive.google.com/drive/folders/YOUR_FOLDER_LINK" target="_blank">Thesis Presentation Deck</a>  
- 📄 Full Paper & Validation Data available on request

<br><br>