# Humanoid Digital Twin – 16-DoF Real-Time Synchronized Control System  
**Authors:** Sudarshan Sridhar, *et al.*  
**Publication:** IEEE – *A Generic System Architecture for the Design and Development of a Humanoid Digital Twin*

## 📌 Overview  
This repository contains the full implementation of a **16-Degree-of-Freedom Humanoid Digital Twin**, designed and built as part of an IEEE-published research project.  
The system provides **real-time synchronized modeling**, **servo-level control**, and **bi-directional feedback** between a physical humanoid and its digital simulation.

This project demonstrates practical skills in:

- Robotics control systems  
- Real-time digital twin architecture  
- Kinematics programming  
- Servo actuation and calibration  
- Python GUI development  
- System integration and modular design  

It also lays the foundation for extending the system into **ROS2**, **LLM-based control**, and **simulation-to-reality pipelines**.

---

## 🏗️ Architecture Overview  
The complete architecture consists of four main modules:

### **1. Servo Control Layer (`Servo_Control.py`)**
- Handles PWM/servo motor angles for all joints  
- Performs range mapping, clamping, calibration  
- Ensures smooth interpolation between poses  
- Abstracts low-level motor commands into easy function calls  

### **2. Humanoid Kinematics Layer (`humanoid_1.py`)**
- Defines joint structure and 16-DoF configuration  
- Stores positional presets  
- Contains the high-level action controller that maps body actions to servo outputs  

### **3. Action Sequencing & Motion Logic (`humanoid_actions.py`)**
- Defines complex humanoid actions such as standing, walking, waving, sitting  
- Executes motion sequences frame-by-frame  
- Handles interpolation for smooth human-like transitions  
- Allows chaining modular actions to form full behaviors  

### **4. GUI Interface (`GUI.py`)**
- Python GUI for controlling the humanoid  
- Provides buttons for actions, presets, and calibration  
- Displays state and debugging information  
- Allows both manual and pre-scripted control workflows  

---

## ✅ Key Features  
- **16-DoF humanoid modeling**  
- **Real-time digital twin synchronization**  
- **Modular control layers** (actions → joint mapping → servo control)  
- **Smooth interpolation** for natural movement  
- **Human-readable presets** for repeatable postures  
- **GUI for intuitive control**  
- **Calibrated servo management**  
- **IEEE research-compliant architecture**  

---

## 🎯 Research Contribution  
This project implements the architecture described in the IEEE paper:

- A modular, scalable digital twin framework  
- Real-time synchronization between physical hardware and virtual model  
- Action-layer design that abstracts low-level commands  
- Kinematic consistency between simulated and physical joints  
- System that can be extended into ROS2 nodes, Gazebo simulations, or LLM-driven controllers  

---

## 🚀 Running the Project

### ✅ Requirements
- Python 3.8+
- Required libraries (install via pip):
```bash
pip install pyserial
pip install tkintertable
