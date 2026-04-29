# Visual Language Maps (VLMaps) 

Visual Language Maps (VLMaps) is a framework that allows robots to navigate through complex environments by **fusing 3D physical data** with semantic "understanding" from vision-language models. Unlike traditional maps that only know where obstacles are, a VLMap knows where specific objects (like "the blue sofa") are located in space.
* https://vlmaps.github.io/

---
### The VLMaps Framework
The core innovation of VLMaps is its ability to create a "language-indexable" map of the world without requiring any manual labeling.

* **Architecture**
    * It uses a vision-language model like LSeg to generate pixel-level embeddings from a robot's video feed. These embeddings are then "back-projected" onto a 3D reconstruction of the environment, essentially labeling the physical world with text-based features.
* **Code as Policies**
    * VLMaps uses Large Language Models (LLMs) to translate natural language commands into **executable Python code**. For example, a command like "go in between the sofa and the TV" is converted into a structured sequence of spatial subgoals that the **robot's navigation stack** can follow.
* **Cross-Embodiment**
    * A single VLMap can be shared across different types of robots. A drone might use it to fly over a table, while a ground robot uses the same map to navigate around it by generating custom obstacle maps on-the-fly.
* **Multimodal Expansion (AVLMaps)**
    * Extended versions like AVLMaps integrate audio and images, allowing robots to find targets based on **sound** (e.g., "go to where you heard the glass break").

---
### Performance Metrics for AI Agents

To rank agents like those using VLMaps, researchers use standardized metrics that measure both effectiveness and efficiency.

* **Success Rate (SR)**
    * The percentage of episodes where the agent successfully reaches the goal within a certain distance (usually 3 meters).
* **Success weighted by Path Length (SPL)**
    * Considered the "gold standard" metric, it measures how efficient the agent's path was compared to the shortest possible path. An agent that reaches the goal but meanders aimlessly will have a high SR but a low SPL.
* **Oracle Success Rate (OSR)**
    * Measures if the agent ever got close to the goal at any point during its trajectory, even if it didn't stop there.
* **Navigation Error (NE)**
    * The average distance (in meters) between the agent's final stopping position and the true target location.
* **Remote Grounding SPL (RGSPL)**
    * Used for tasks where the agent must stop near an object it cannot see at the start, rewarding both correct localization and path efficiency.
* **Embodied Metrics**
    * Newer benchmarks like VLN-PE track physical performance, such as Fall Rate (FR) for legged robots and Stuck Rate (StR) for agents immobilized by obstacles.
