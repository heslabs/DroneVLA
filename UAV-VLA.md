# UAV-VLA: Vision-Language-Action System for Large Scale Aerial Mission Generation

* **Codebase**: The official repository containing the framework implementation and simulation code is on GitHub at sautenich/uav-vla.
  * https://github.com/sautenich/uav-vla
* **Benchmark**: They utilize the UAV-VLPA-nano-30 benchmark, which consists of high-resolution satellite images for evaluating linguistic mission interpretation.
  * https://arxiv.org/html/2501.05014v2

### Abstract
The UAV-VLA (Visual-Language-Action) system is a tool designed to facilitate communication with aerial robots. By integrating satellite imagery processing with the Visual Language Model (VLM) and the powerful capabilities of GPT, UAV-VLA enables users to generate general flight paths-and-action plans through simple text requests. This system leverages the rich contextual information provided by satellite images, allowing for enhanced decision-making and mission planning. The combination of visual analysis by VLM and natural language processing by GPT can provide the user with the path-and-action set, making aerial operations more efficient and accessible. The newly developed method showed the difference in the length of the created trajectory in 22% and the mean error in finding the objects of interest on a map in 34.22 m by Euclidean distance in the K-Nearest Neighbors (KNN) approach.

https://arxiv.org/abs/2501.05014

This repository includes:
* The implementation of the UAV-VLA framework.
* Dataset and benchmark details.
* Code for simulation-based experiments in Mission Planner.
