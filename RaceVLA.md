# RaceVLA: VLA-based Racing Drone Navigation with Human-like Behaviour (DATASET)

Valerii Serpiva, Artem Lykov, Artyom Myshlyaev, Muhammad Haris Khan, Ali Alridha Abdulkarim, Oleg Sautenkov, Dzmitry Tsetserukou
* Arxiv: https://arxiv.org/abs/2503.02572 
* GitHub: https://github.com/SerValera/RaceVLA

---
## RaceVLA

Features
* Drone initialization and takeoff procedures
* Communication setup between drone and RaceVLA server
* RaceVLA model inference handling on the server side
* Data exchange scripts to process and send image from onboard camera and receive control commands from the RaceVLA model

### System Overview
The project integrates:

* Visual-Inertial Odometry (VIO) for state estimation using open_vins
* FishEye T265 with Intel RealSense realsense-ros
* Flight control using ArduPilot firmware (v4.4.4) running on a SpeedyBee F4 V4 flight controller.
* ROS 1 for data handling, visualization, and control logic.
* Flask for transferring data between the drone and a remote server.


### Tested Environment
* Platform: Intel NUC
* OS: Ubuntu 22.04
* Flight Controller: SpeedyBee STM32F405 ARM
* Firmware: ArduPilot v4.4.4
* Middleware: ROS 1 (Noetic)
* Communication Framework: Flask (Python-based server)
