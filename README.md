# DroneVLA: VLA based Aerial Manipulation





---
### Overview of the VLA based aerial manipulation and Path Planning Architecture

<img width="850" height="453" alt="image" src="https://github.com/user-attachments/assets/f269112f-4551-4ebd-93ae-a5af89a9365c" />

---
### Resource

* DroneVLA: VLA based Aerial Manipulation [[PDF]](https://www.researchgate.net/publication/399956688_DroneVLA_VLA_based_Aerial_Manipulation/download?_tp=eyJjb250ZXh0Ijp7ImZpcnN0UGFnZSI6InB1YmxpY2F0aW9uIiwicGFnZSI6InB1YmxpY2F0aW9uIn19)
  * https://www.researchgate.net/figure/Human-Localization-and-Navigation-by-drone_fig1_399956688
  * This work introduces a novel concept of autonomous aerial manipulation system capable of interpreting high-level natural language commands to retrieve objects and deliver them to a human user. The system is intended to integrate a MediaPipe based on Grounding DINO and a Vision-Language-Action (VLA) model with a custom-built drone equipped with a 1-DOF gripper and an Intel RealSense RGB-D camera.
* RaceVLA: VLA-based Racing Drone Navigation with Human-like Behaviour
  * https://arxiv.org/html/2503.02572v1
  * RaceVLA presents an innovative approach for autonomous racing drone navigation by leveraging Visual-Language-Action (VLA) to emulate human-like behavior. This research explores the integration of advanced algorithms that enable drones to adapt their navigation strategies based on the real-time environmental feedback, mimicking the decision-making processes of human pilots. The model, fine-tuned on a collected racing drone dataset, demonstrates strong generalization despite the complexity of the drone racing environments


---
## Core Concepts of VIO Navigation

VIO works by fusing two distinct types of data to determine the device's pose (position and orientation): 
 
Visual Odometry (VO): Cameras track features in the surrounding environment from frame to frame to estimate movement.
Inertial Measurement Unit (IMU): Sensors like accelerometers and gyroscopes monitor motion, acceleration, and rotation rates.
Sensor Fusion: Algorithms such asKalman filters integrate these inputs to compensate for each other's weaknesses, such as lighting issues (visual) or sensor bias/drift (inertial). 
 
