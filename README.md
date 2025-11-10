# Humanoid Digital Twin – 16-DoF Real-Time Synchronized Control System  
### IEEE Published Architecture • Python-Based Control • Real Hardware Integration

---

## 📘 Abstract  
This repository contains the implementation of the **Humanoid Digital Twin (HDT)** system described in the IEEE paper  
**"A Generic System Architecture for the Design and Development of a Humanoid Digital Twin"**.

The system establishes a **bidirectional synchronization loop** between a 16-DOF physical humanoid robot and its digital replica, enabling real-time mirroring of servo behavior, body configuration, kinematics, and action sequences.  
The architecture separates high-level motion logic, pose mapping, servo control, and GUI interaction, providing modularity, extensibility, and stable human-like motion generation.

---

## 🏗️ System Architecture  

The HDT system follows a **layered control architecture**, as described in the IEEE paper:

### ✅ 1. Action Sequencing Layer (`humanoid_actions.py`)  
- Implements high-level actions (stand, walk, wave, sit).  
- Generates smooth transitions between poses using interpolation.  
- Converts human-readable behaviors into joint-level commands.

### ✅ 2. Kinematic Mapping Layer (`humanoid_1.py`)  
- Defines humanoid structure and 16-DOF joint model.  
- Stores kinematic constraints, joint limits, and pose presets.  
- Ensures coherent body posture and safe motion range.

### ✅ 3. Servo Execution Layer (`Servo_Control.py`)  
- Controls all servo motors with calibrated offsets.  
- Smooths trajectory execution to avoid jitter or abrupt motion.  
- Handles angle clamping, speed ramping, and PWM mapping.

### ✅ 4. Graphical User Interface (`GUI.py`)  
- Real-time control interface for executing actions.  
- Displays presets, servo states, and debugging information.  
- Enables manual and scripted control workflows.

---

## 🔩 16-DoF Humanoid Layout  

Per the IEEE design specification:  
- **Upper Body (8 DOF)**  
  - Shoulders (2 each), Elbows (1 each), Neck (1), Torso pivot (1)

- **Lower Body (8 DOF)**  
  - Hips (2 each), Knees (1 each), Ankles (1 each)

This configuration enables balanced stance, coordinated leg motion, and expressive arm gestures.

---

## 🔁 Dataflow Overview  

The HDT architecture uses a clean **software → hardware → feedback** loop:

1. GUI receives user command  
2. Action Sequencer expands motion into joint frames  
3. Kinematic Layer converts frames into servo angles  
4. Servo Layer executes movement on robot  
5. Robot performs motion  
6. Optional feedback updates digital twin state  

The separation ensures maintainability and scalability.

---

## ⚙️ Hardware–Software Interaction  

The IEEE architecture decomposes the system into:

### **Software Layer**
- GUI  
- Action planner  
- Pose manager  
- Kinematic processor  

### **Hardware Layer**
- Microcontroller with PWM output  
- Servo motors  
- Power subsystem  
- Optional IMU/sensors  

This modularity allows future upgrades such as ROS2 nodes or simulation environments.

---

## 🧮 Stability, Interpolation & COG Control  

The IEEE paper emphasizes:

- Smooth interpolation between pose frames  
- Safe transition enforcement  
- Center-of-gravity (COG) stability during standing/walking  
- Joint-range constraints  
- Gradual hip–knee–ankle shifting for stable gait  

These mechanisms ensure reliable humanoid balance across all actions.

---

## 📊 Performance Summary  
(From IEEE evaluation)

| Metric                                   | Value                |
|------------------------------------------|----------------------|
| Average servo latency                    | **50–80 ms**         |
| GUI → motion command delay               | **<100 ms**          |
| Full walk cycle execution                | **≈ 4.2 seconds**    |
| Calibration error                        | **< 2.5° average**   |

These results confirm stable synchronization between the digital twin and real hardware.

---

## ✅ Key Features  
- 16-DOF full-body humanoid model  
- Real-time synchronized digital twin  
- Modular architecture (actions → kinematics → servo)  
- Python GUI for control and testing  
- Smooth interpolation system  
- IEEE-based architecture  
- Easy extension to ROS2, Unity, or RL controllers  

---

## 📦 Repository Structure  

Humanoid-Digital-Twin/
│── GUI.py
│── humanoid_1.py
│── humanoid_actions.py
│── Servo_Control.py
│── motor_move.py
│── calib_value.txt
│── Presets.txt
│── save_data.txt
│── Presets/
└── testwalk.txt

---

## 🚀 Running the Project  

### ✅ Install Requirements  

pip install pyserial
pip install tkintertable

### ✅ Run Specific Modules  

python humanoid_actions.py
python Servo_Control.py

---

## 🧭 Future Extensions  
- ROS2 integration for robotics pipelines  
- Unity/Gazebo simulation-based digital twin  
- LLM-based high-level control (Qwen/Gemini)  
- Sensor-driven real-time feedback  
- Reinforcement learning for autonomous behavior generation  
- Web dashboard for remote operation  

---

## 📚 Reference  
**IEEE Paper:** *A Generic System Architecture for the Design and Development of a Humanoid Digital Twin*  
https://ieeexplore.ieee.org/document/10983996

 

