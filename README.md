# Localisation-system-MONA-robot
This repository explains how to install the Whycon localisation system for robotics experiments using (ROS noetic) and Ubuntu 20.04.
To start working on the 'whycon' system and MONA robot by running some hardware experiments, you need to follow the steps in the following files by order:
1. **Localisation System Setup.**
2. **Python_prep_MONA.**
3. **Arduino Setup and Implementation.**

<img src="https://github.com/user-attachments/assets/da198a80-69ef-4193-a7b3-07fc21da8bb9" width="600" height="400">

In the image above:
- (a) The camera detects the tags of the MONA robots via the whycon system and determines the current positions.
- (b) The position data will be processed, and the motors' speeds will be generated and sent via Wi-Fi.
- (c) The router that transfers the data to the MONA.
- (d) MONA robots will receive their speeds through the Wi-Fi module, then they move to their new positions in the arena.


## Reference:
1. Bahaidarah, M., Rekabi-Bana, F., Marjanovic, O., Arvin, F.: Swarm flocking using optimisation for a self-organised collective motion. Swarm and Evolutionary Computation p. 101491 (2024)
