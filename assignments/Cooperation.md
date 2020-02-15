## Cooperation domain

You will use PDDL 3.1 to express preferences and constraints. 
Let's consider the scenario of exploring a surface with a system formed by  an Unmanned Aerial Vehicle (UAV) and an Unmanned Ground Vehicle (UGV). The goal is to reach a set of target points (TPs) and send images of them. 

We define the following actions:
 - Dock or Undock from the base station.
 -  Move between locations with a defined navigation mode. There are two possible values: N0 and N1. When the value is N1 the speed is double than when the value is N0.
 -  Take photographs with the camera. Tha camera has two rotations:  up and down (PAN) and left and right (TILT).
 -  Change the navigation mode.
 -  Transmit the images taken.
 -  Change the orientation.
 
 All the actions have a variable duration (except when trasmitting a picture, changing the navigation mode and Docking that are constant) and consume energy.

The initial state is as follows:
 -  Declare the distances between all defined locations.
 -  Define the rotation of the allowed orientation between adjacent positions.
 -  The UGV is in position X=6 Y=10 and the UAV in X=10 Y=2, each robot at its base station.
 - Navigation mode of both agents is N0.
 -  Each robotic system has an on board camera, with an initial orientation equal to  Pan = 0 and Tilt = 0.
 -  Definition of functions to control the energy, the total distance travelled and duration of the actions.

As a baseline of the objects defined in the problem, consider this definition:
  ```
 (:objects
 ; Decide how to represent X,Y locations
  Leader - UGV
  Follower0 - UAV
  N0 N1 - NavMode
  P_0 P_45 P_90 P_135 P_180 P_225 P_270 P_315 - Pan
  T_0 T_45 T_90 T_270 T_315 - Tilt
 ```
 
The goal is to take two pictures in the following positions:
  ```
X=5 Y=9 with P_0 & T_0
X=16 Y=13 with P_0 & T_0
  ```
  minimizing the total duration and/or the energy used. 

Define two preferences:
 -  ALWAYS the UAV does not remain at the base station.
 -  SOMETIMES the UGV does not remain at the base station.
 
 Then, define a constrain that combines and gives different weights to both preferences.
