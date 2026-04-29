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
