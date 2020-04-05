# Integrate path-planning and task-planning

## Objectives

* Compare Dijkstra, A* and Theta* algorithms.
* Implement Theta* and some heuristics.
* Compare the heuristics and understand the impact on the solution.
* Use a graphical interface to visualize the results.
* Integrate path-planning and task-planning.


## Dependencies

Install [PathPlanPrinter](https://github.com/R012/PathPlanPrinter), which depends on the libraries numpy and PIL or Pillow. Read the README.md file in the project's root folder for instructions about the usage and how to download it from GitHub.


## Practical assignment

### Path-planning
Perform the following tasks:

1. Consider that the robot is initially located at the position (18,19) and the goal is to be at position (12,12). Visualizes the computed path using the Dijkstra algorithm. Change the initial point to  (27,19) and the goal point to (8,20).
   
2. We provide you with the implementations of A* and Dijkstra in the ```/src/``` folder. The implementation of A* is based on the  pseudo-code of the next figure taken from [Theta*: Any-Angle Path Planning on Grids](https://arxiv.org/pdf/1401.3843.pdf):

<img align="center" src="A*.png" width="600">

3. Implement Theta* using the following pseudo-code:

<img align="center" src="Theta*.png" width="600">

Take into account that the difference between A* and Theta* is the Line of sight. Here is the code to calculate it:

<img align="center" src="Lineofsight.png" width="600">

4. Which heuristic is used by default? If needed, use the path-planning visualizer in https://qiao.github.io/PathFinding.js/visual/ to reconstruct the scenario and observe the node expansion using different algorithms.

5. Implement the Euclidean, Manhattan and Octile heuristics for A*/Theta*. These functions take the initial and final points as tuples (X, Y) and must return a float with the heuristic value.

6. Run the 3 algorithms and compare the results, changing when appropriate the heuristic. 

### Integration

Once the path-planning algorithms are ready, we want to call them to avoid the PDDL planner to calculate paths between tasks. Do the following tasks:

1. Modify the [Planetary exploration on Mars](https://github.com/Malola2015/planningCourse/blob/master/assignments/PlanetaryExploration.md) or the [Cooperation](https://github.com/Malola2015/planningCourse/blob/master/assignments/Cooperation.md) domain to consider the coordinates as objects of the type ```Point```. For example, X=6 Y=10 will be represented as the object P0610. Now, you can delete all the obstacles since the path will be now delegated to the path-planner algorithm, freeing the PDDL planner from it.

2. Run the new domain (if you have modelled it in a different way) and save the solution into a file called ```planning.txt```. This file will be the input to an integration program that will call the path-planning algorithm.

3. Copy the code provided in the following link to a file called ```run_integration.py```. 

   https://gist.github.com/R012/0fe8ec73b58c0a95844370c6510454d9

4. That code reads the PDDL output, and each time there is a ```move``` action with a coordinate, it calls the path-planning algorithm with the destination given by the action. By default, the initial state is set to the position = (10, 10) in the ```visualize_paths_from_pddl``` function. Please change it accordingly to your initial state in your PDDL file.

5. Note that you have to provide the route and names to both, the solution of the planner, i.e.```planning.txt``` (placed in this case in the ```/res/``` folder) and the map with the obstacles, i.e.```example.png``` (placed in the same folder). You can place those files when you want, just remember to specify the route. The code that you have to modify is:

``` task_plan = generate_task_list('../res/planning.txt')``` 
```visualize_paths_from_pddl(task_plan, '../res/example.png')``` 

5. Run the ```run_integration.py``` file and see the result. 

6. Change the heuristics and the algorithms.


### What else?

Write in a .doc file, if what you have implemented so far is enough to autonomously control the robot. what else is needed? You don´t need to implement anything, it is more a reflexion for building intelligent robots. 



