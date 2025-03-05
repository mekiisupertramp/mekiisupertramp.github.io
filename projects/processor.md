---
layout: project
type: project
title: "Custom CPU for robot control [...in progress...]"
image: img/processor/pro_logo.png
date: 2016
published: true
labels:
  - FPGA
  - Logisim
  - ALU
  - Basys 2
summary: "Building a CPU from scratch using Logisim for designing and simulating logic circuit."
---

# Introduction 
The primary goal of this project is to implement a CPU in an FPGA for controlling a robotic system. The focus is to develop a responsive robot capable of adjusting its motor speeds based on proximity detection, creating an intuitive hand-gesture control interface.

The system architecture comprises two main components:
- A user-facing control unit equipped with left and right distance sensors, implemented on a Basys FPGA board.
- The robotic platform with independent wheel motors (Moteur_G and Moteur_D), driven by a secondary Basys board that receives wireless commands via Bluetooth/Wi-Fi.
- Key operational logic allows dynamic speed modulation – approaching a sensor accelerates the corresponding motor, while withdrawing slows it. Though initially focused on distance-based motion control, the modular design accommodates future enhancements including:
- Wheel speed sensors (capt_vitesse_G/D) for real-time velocity feedback displayed on 7-segment units
- Collision avoidance via obstacle and limit sensors (capt_obst, fin_course)

This project emphasizes practical applications of embedded systems, wireless communication protocols, and sensor-motor feedback loops, while maintaining scalability for additional features through its FPGA-based architecture.

<p align="center">
<img class="img-fluid" src="../img/mandelbrot/timing_v2.png" > 
</p>

# Conclusion
