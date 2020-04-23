# Integrate path-planning and task-planning 


## Objectives

* Compare Dijkstra, A* and Theta* algorithms.
* Implement Theta* algorithm and some heuristics. 
* Compare the heuristics and understand the impact on the solution.
* Use the R2P2 simulator.
* Integrate path-planning and task-planning.

## Dependencies

Install the [R2P2](https://github.com/ISG-UAH/R2P2) simulator, which depends on the libraries numpy and matplotlib. Read the README.md file in the project's root folder for instructions about the simulator installation and usage.

Remember to install R2P2 dependencies by executing ```pip install -r requirements.txt``` from the folder that contains R2P2.

## Practical assignment

### Path-planning

Perform the following tasks:

1. Get familiar with the R2P2 simulator. Run the simulator with the command `python r2p2.py`. It will create a plain scenario with a robot teleoperated by the arrows keys.

2. Run the Path Planning scenario as follows:

   ```
   python r2p2.py --scenario ../conf/scenario-pathplanning.json
   ```

   Note that the robot is initially located at the position (18,19) and the goal at position (12,12). The simulator visualizes the computed path. 
   
3. Given that the configuration of the robot controller is located in the file ```conf/controller-pathplanning.json```, change the initial point to  (27,19) and the goal to (8,20). You can also change the size of the grid. Remember that it is advisable 
to use values between 15 and 40 in order not to lose precision without compromising efficiency.

4. In order to change the algorithm (A*, Dijkstra or Theta*) just set "A*"  "Dijkstra" or "Theta*" in the ```algorithm``` field of ```conf/controller-pathplanning.json``` (caution, the simulator is case sensitive). We provide you with the implementation of A* and Dijkstra. The implementation of A* is based on the  pseudo-code of the next figure:

<img align="center" src="A*.png" width="600">

5. Implement Theta* using the following pseudo-code:

<img align="center" src="Theta*.png" width="600">

Take into account that the difference between A* and Theta* is the Line of sight. Here is the code to calculate it:

<img align="center" src="Lineofsight.png" width="600">

6. Which heuristic is used by default? If needed, use the path-planning visualizer in https://qiao.github.io/PathFinding.js/visual/ to reconstruct the scenario and observe the node expansion using the different algorithms.

7. Implement the Manhattan, Octile and Euclidean heuristics for A*/Theta*. Go to the ```r2p2/heuristic.py``` file and fill out the functions ```euclidean``` and ```manhattan```, and create a new one for the Octile heuristic (don´t forget to register it). The functions take the initial and final points as tuples (X, Y) and must return a float with the heuristic value.

8. Create the image given on [slide 19](https://github.com/Malola2015/planningCourse/blob/master/robotics/pathplanning.pdf), set the grid size as 40, run the 3 algorithms and compare the results, changing the heuristic. Capture the images of the solution and upload them with the rest of the files.

### Integration

Once the path-planning algorithms are ready, we want to call them to avoid the PDDL planner to calculate paths between actions. Do the following tasks:

1. Modify the [Cooperation](https://github.com/Malola2015/planningCourse/blob/master/assignments/Cooperation.md) domain to consider the coordinates as objects of the type Point. For example, X=6 Y=10 will be represented as the object P0610. Now, you can delete all the obstacles since the path will be now delegated to the path-planner algorithm, freeing the PDDL planner from it.

2. Run the new domain (if you have modelled it in a different way) and save the solution into a file called ```planning.txt```. This file will be the input to the simulator that will call the path-planning algorithm.  This file is located in ```../res/``` folder. Just overwrite it.

3. The code provided in the following link is placed in ```r2p2/controllers/pddl_executor.py```.

   https://gist.github.com/R012/244f4e97416adcb8f8716caf28d19f2e

   It reads the PDDL output, and each time there is a ```move``` action with a coordinate, it calls the path-planning  
   algorithm with the destination given by the action. This code is integrated in the simulator.

4. Change the heuristics and the algorithms in the appropiate function.

5. Run the planning domain scenario using the simulator.

   ```python r2p2.py --scenario ../conf/scenario-planning.json```

### What else?

Write in a .doc file if what you have implemented so far is enough to autonomously control the robot. What else is needed? You don´t need to implement anything (but you can do it if you want), it is more a reflexion for building intelligent robots from the planning and execution point of view.
