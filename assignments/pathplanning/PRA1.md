# Implementation and comparison of heuristics for path-planning


## Objectives

* Compare Dijkstra, A* or Theta*algorithms.
* Implement Theta* and some heuristics.
* Understand the impact of the heuristic selection in path-planning.
* Use the R2P2 simulator.

## Dependencies

Install the [R2P2](https://github.com/ISG-UAH/R2P2) simulator, which depends on the libraries numpy and matplotlib. Read the README.md file in the project's root folder for instructions about the simulator installation and usage.

Remember to install R2P2 dependencies by executing ```pip install -r requirements.txt``` from the folder that contains R2P2.

## Practical assignment

Perform the following tasks:

1. Get familiar with the R2P2 simulator. Run the simulator with the command `python r2p2.py`. It will create a plain scenario with a robot teleoperated by the arrows keys.

2. Run the Path Planning scenario as follows:

   ```
   python r2p2.py --scenario ../conf/scenario-pathplanning.json
   ```

   Note that the robot is initially located at the position (18,19) and the goal at position (12,12). The simulator visualizes the computed path. 
   
3. Given that the configuration of the robot controller is located in the file ```conf/controller-pathplanning.json```, change the initial point to  (27,19) and the goal point to (8,20).

4. In order to change the algorithm (A*, Dijkstra or Theta*) just set "A*"  "Dijkstra" or "Theta*" in the ```algorithm``` field of ```conf/controller-pathplanning.json``` (caution, the simulator is case sensitive). We provide you with the implementation of A* and Dijkstra. The implementation of A* is based on the  pseudo-code of the next figure:

<img align="center" src="A*.png" width="400">

5. Implement Theta* using the following pseudo-code:

<img align="center" src="Theta*.png" width="400">

Take into account that the difference between A* and Theta* is the Line of sight. Here is the code to calculate it:

<img align="center" src="Lineofsight.png" width="400">

6. Which heuristic is used by default? If needed, use the path-planning visualizer in https://qiao.github.io/PathFinding.js/visual/ to reconstruct the scenario and observe the node expansion using different algorithms.

7. Implement the Manhattan and Euclidean heuristics for A*/Theta*. Go to the ```r2p2/heuristic.py``` file and fill out the functions ```euclidean``` and ```manhattan```. Both functions take the initial and final points as tuples (X, Y) and must return a float with the heuristic value.

8. Run the 3 algorithms and compare the results, changing when appropriate the heuristic.