We are going to extend the GRIPPER domain (the first domain studied in class) to use time and preferences. This extension of the domain was part of the June exam in 2020.

https://github.com/Malola2015/planningCourse/blob/master/assignments/Gripper.md

Do the following steps:
 1. Consider that the rooms where the robot of the GRIPPER domain moves are kitchen and living room; and that the robot is initially in the kitchen, together with two balls Z1 and Z2. 
    We want as a goal that the balls and the robot to be in the living room. Model this new situation in the corresponding file.
 2. Extend the `pick-up` and `drop` actions to have a duration that depends on the weight of the ball. Name that predicate as `dur-ball`. 
 3. Add a preference that expresses that the robot is at the end in the living room.
 4. Comment the previous preference and add another preference that expresses that the robot is sometime in another room called `bathroom`. 
