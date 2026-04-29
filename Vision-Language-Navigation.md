# Vision-Language Navigation (VLN)

Vision-Language Navigation (VLN) is an interdisciplinary field within Embodied AI that tasks an autonomous agent with navigating through a 3D environment using only visual observations and natural language instructions. Unlike traditional GPS navigation, VLN requires the agent to understand relative spatial commands like "go down the hallway and turn left at the painting" while identifying landmarks in real-time.

---
### Core Task Types
Researchers categorize VLN tasks based on the nature of the instruction and the environment:

* **Instruction-Oriented**: The agent must strictly follow a specific path described in the text (e.g., "walk past the sofa, enter the kitchen, and stop by the fridge").
* **Goal-Oriented**: The agent is given a target object or room and must find its own way there (e.g., "find the remote").
* **Dialogue-Based**: The agent can engage in multi-turn conversations to clarify ambiguous instructions or ask for help when lost (e.g., CVDN).

---
### Key Frameworks & Approaches
Current research is shifting from simple "observe-and-reason" models to more complex reasoning architectures:

* **Foundation Models (LLMs/VLMs)**: Recent frameworks like VLN-R1 and VL-Nav use Large Vision-Language Models to translate video streams directly into navigation actions through reinforcement learning.
* **Visual-Language Maps (VLMaps)**: These systems build a spatial map that fuses visual-language features with 3D reconstructions, allowing robots to index the physical world with open-vocabulary commands like "park between the sofa and the TV".
* **Generative Imagination**: Tools like VISTA use diffusion models to "imagine" the target destination based on local observations, helping the agent stay aligned with long-horizon instructions.

---
### Evaluation Benchmarks
Performance is typically measured in simulated environments before real-world deployment:

* **Room-to-Room (R2R)**: A standard benchmark for indoor navigation featuring human-annotated instructions and Matterport3D house scans.
* **VLN-CE**: A version for continuous environments where agents move freely rather than jumping between predefined nodes.
* **AerialVLN**: A newer domain focusing on unmanned aerial vehicles (UAVs) navigating city-scale 3D spaces.

---
### Major Challenges

* **Sim-to-Real Gap**: Models often perform well in simulations like Habitat but struggle with the noisy sensory data and dynamic obstacles (like moving people) found in the real world.
* **Spatial Reasoning**: Bridging the "modality gap" between abstract text (concepts) and raw pixels (visuals) remains difficult, especially for complex trajectories

---
## Visual Language Maps (VLMaps) 

Visual Language Maps (VLMaps) is a framework that allows robots to navigate through complex environments by fusing 3D physical data with semantic "understanding" from vision-language models. Unlike traditional maps that only know where obstacles are, a VLMap knows where specific objects (like "the blue sofa") are located in space.
* https://vlmaps.github.io/

---
### The VLMaps Framework
The core innovation of VLMaps is its ability to create a "language-indexable" map of the world without requiring any manual labeling.

* **Architecture**: It uses a vision-language model like LSeg to generate pixel-level embeddings from a robot's video feed. These embeddings are then "back-projected" onto a 3D reconstruction of the environment, essentially labeling the physical world with text-based features.
* **Code as Policies**: VLMaps uses Large Language Models (LLMs) to translate natural language commands into executable Python code. For example, a command like "go in between the sofa and the TV" is converted into a structured sequence of spatial subgoals that the robot's navigation stack can follow.
* **Cross-Embodiment**: A single VLMap can be shared across different types of robots. A drone might use it to fly over a table, while a ground robot uses the same map to navigate around it by generating custom obstacle maps on-the-fly.
* **Multimodal Expansion (AVLMaps)**: Extended versions like AVLMaps integrate audio and images, allowing robots to find targets based on sound (e.g., "go to where you heard the glass break").

---
### Performance Metrics for AI Agents

To rank agents like those using VLMaps, researchers use standardized metrics that measure both effectiveness and efficiency.

* **Success Rate (SR)**: The percentage of episodes where the agent successfully reaches the goal within a certain distance (usually 3 meters).
* **Success weighted by Path Length (SPL)**: Considered the "gold standard" metric, it measures how efficient the agent's path was compared to the shortest possible path. An agent that reaches the goal but meanders aimlessly will have a high SR but a low SPL.
* **Oracle Success Rate (OSR)**: Measures if the agent ever got close to the goal at any point during its trajectory, even if it didn't stop there.
* **Navigation Error (NE)**: The average distance (in meters) between the agent's final stopping position and the true target location.
* **Remote Grounding SPL (RGSPL)**: Used for tasks where the agent must stop near an object it cannot see at the start, rewarding both correct localization and path efficiency.
* **Embodied Metrics**: Newer benchmarks like VLN-PE track physical performance, such as Fall Rate (FR) for legged robots and Stuck Rate (StR) for agents immobilized by obstacles.
