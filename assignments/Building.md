## Building

There is a building with N + 1 floors, numbered from 0 to N. 
The building has *K*  fast (accelerating) elevators that stop only in floors that are multiple of M/ 2 (so *M* has to be an **even** number). Furthermore, within each building, there are *L* slow elevators, that stop at every floor of the building. 

There are several persons, for which their current location (i. e., the floor they are) and their destination are given. The planning problem is to find a plan that moves the persons to their destinations while it minimizes the total duration.

The actions are described next:

 - Move up (lift, level1, level2): the lift moves up from level1 to level2. Model two actions, one for a fast lift and another one for a slow lift. The duration of the 2 actions should be given by a predicate. 
 - Move down (lift, level1, level2): the lift moves down from level1 to level2. Model two actions, one for a fast lift and another one for a slow lift.  The duration of the 2 actions should be given by a predicate.
 - Board (person, lift, level, num1, num2): the person boards on a level. The variable num1 specify the number of persons in the lift, and num2 is incremented in 1 when the person is boarded. The duration of the action is constant and equal to 1.
 - Leave (person, lift, level, num1, num2): the person leaves the lift on a floor level. The variable num1 specifies the number of persons in the lift, and num2 is decremented when the person leaves the lift. The duration of the action is constant and equal to 1.
 - Sanitize (lift): it performs an elevator cleaning. As a precondition, the lift will not be disinfected, and as an effect, it will be. Also modify the Board operator so that it has as a precondition that the elevator must be disinfected.

Note: Use objects (and not numbers) to treat the number of persons and the level floors. That is, define the following types:
```
  (:types  lift - object 
           slowlift fastlift - lift
           person - object
           number - object
  )
```
and in the initial state use the following for representing *level*, *num1* and *num2*:

```
(:objects 
   n0 n1 n2 n3 n4 n5 n6 n7 n8  - number
...
)
```

Model two problems. The first one with 5 levels, 2 lifts of each type and 2 persons. The second problem has 9 levels, 4 persons and 2 lifts of each type.
