# DroneVLA: VLA based Aerial Manipulation

Vision-Language-Action (VLA) models represent a paradigm shift in drone navigation by enabling Unmanned Aerial Vehicles (UAVs) to generate direct control signals (like velocity and yaw commands) from **visual inputs and natural language instructions**. Unlike traditional systems that rely on separate modules for planning and execution, VLA-based navigation integrates perception and action into a single end-to-end framework. 
 

### Key VLA Models for Drones
Research in 2025 and 2026 has introduced several specialized VLA models for different aerial tasks:

* **RaceVLA**: Specifically designed for autonomous racing, this model uses First-Person View (FPV) video and text commands to mimic the high-speed decision-making of human pilots. It outperforms general-purpose models like OpenVLA in motion and semantic generalization.
* **AutoFly**: An end-to-end model for navigation in unknown outdoor environments that uses a pseudo-depth encoder to derive spatial features from standard RGB cameras, improving 3D reasoning.
* **DroneVLA**: Focuses on aerial manipulation (fetch-and-carry tasks), using VLA for grasping logic while relying on deterministic visual servoing for safe navigation and handover to humans.
* **CognitiveDrone**: A dual-model framework that separates low-level flight control from high-level cognitive reasoning, significantly improving success rates in complex tasks requiring logical inference.
* **VLA-AN**: A lightweight model optimized for onboard deployment on resource-constrained UAVs, achieving high inference throughput and using geometric safety corrections to prevent collisions. 
 
### Core Technical Challenges
Implementing VLAs for drones is more difficult than for ground robots due to the "Dynamics Gap": 
 
* **Underactuation**: Drones are underactuated systems where thrust and attitude are coupled; small errors in control can lead to crashes.
* **Real-time Constraints**: High-speed flight requires extremely low latency (often sub-5 ms inference) to ensure timely navigation updates.
* **Sim-to-Real Gap**: Training data from stable, tabletop environments (like Open X-Embodiment) does not easily transfer to the dynamic, 6-DOF movement of aerial flight. 
 
### Emerging Solutions
To overcome these challenges, researchers are employing several innovative strategies:
* **Physics-Guided Transfer**: Injecting payload-aware mechanisms into the model's sampling process to account for physics during inference.
* **3D Gaussian Splatting (3D-GS)**: Used to generate highly realistic synthetic training data to bridge the data domain gap and improve navigation success.
* **Action Chunking**: Predicting a sequence of future actions in a single forward pass to improve temporal consistency and smoothness. 
 

---
## Codebases and Datasets Examples

You can find the resources for these specialized drone models below. Most of them are built on top of OpenVLA, which is the standard open-source framework for fine-tuning vision-language-action models for robotics. 
 
### RaceVLA (High-Speed Racing)
This is the first VLA specifically designed for racing drones, converting FPV video and text into velocity and yaw commands. 
 
* Project Page & Code: You can access the code and pretrained weights on the official RaceVLA Project Page.
* Dataset: The training data, featuring human-piloted racing trajectories, is available on Hugging Face (RaceVLA_dataset). 

### UAV-VLA / UAV-VLPA (Mission Planning) 
These systems focus on high-level mission generation and path planning using satellite imagery and natural language. 
 
* Codebase: The official repository containing the framework implementation and simulation code is on GitHub at sautenich/uav-vla.
* Benchmark: They utilize the UAV-VLPA-nano-30 benchmark, which consists of high-resolution satellite images for evaluating linguistic mission interpretation. 
 
### CognitiveDrone (Advanced Reasoning) 
This model adds a reasoning module to handle complex logic before generating control signals. 
 
* Resources: The model and its dedicated evaluation benchmark, CognitiveDroneBench, can be found in the CognitiveDrone GitHub/Hugging Face repository. 


### Other Useful Datasets
If you are looking for raw aerial data to train your own custom VLA:
* Det-Fly: Over 13,000 images for UAV-to-UAV tracking and detection.
* WildUAV: High-resolution RGB and depth data for aerial perception tasks.
* TII Drone Racing Dataset: Fully-annotated racing data for learning-based navigation. 
 
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

Visual-Inertial Odometry (VIO) camera navigation is a technology that combines data from cameras and Inertial Measurement Units (IMUs) to accurately track the position, orientation, and motion of a device in 3D space. It is essential for navigation in GPS-denied environments—such as indoors, underground, or under tree canopies—where traditional positioning systems fail. 
 
This video demonstrates how VIO allows drones to navigate without GPS:
* GPS free drone navigation with VIO
* https://www.youtube.com/watch?v=BKAy5lTHssI&t=22s


VIO works by fusing two distinct types of data to determine the device's pose (position and orientation): 
 
* Visual Odometry (VO): Cameras track features in the surrounding environment from frame to frame to estimate movement.
* Inertial Measurement Unit (IMU): Sensors like accelerometers and gyroscopes monitor motion, acceleration, and rotation rates.
* Sensor Fusion: Algorithms such asKalman filters integrate these inputs to compensate for each other's weaknesses, such as lighting issues (visual) or sensor bias/drift (inertial). 
 
