## Moving out

This domain aims to move out things (or objects) from one place to another. It involves transportation of those objects between the defined locations using a container whose effects involve universal quantification (all objects are moved) and conditional effects (if the objects are inside the container when it is moved). For that, add the keyword *:conditional-effects* in the requirements as well as durations and types, that is: 

```
    (:requirements :typing :equality :durative-actions :conditional-effects :fluents)
```

Define the following 3 actions, two of them (Move-container and Put-in) should follow the PDDL1.2 syntax while the Take-out action should follow the PDDL2.X syntax. The actions definition is as follows:

 - Move-container: it specifies that the container, modelled as a **constant**, can be moved between two locations. The preconditions dictate that the container must initially be in the starting location for the action to be legal and that it is illegal to try to move the container to the place where it is initially. The effect stays that the container moves to its destination (no longer where it started) and everything inside the container is likewise moved. Note: use *forall* and *when*.
 - Put-in: as a precondition the object that we want to put inside the container should be different to the container. If the action is attempted *when* the object is not at the same place as the container, then there is no effect.
 - Take-out: this action provides a way to remove something from the container, and we will consider that this action has a duration that depends on the object we want to remove from the container.

For the problem, consider two locations Alcala and Madrid, and 3 objects: d, p and m.

```
   (:init (at Container Alcala) (at d Alcala) (in p) (at m Madrid)
          ;Take out durations for each object
   )
  (:goal (and (at Container Madrid)
              (at d Madrid) 
              (at p Alcala)
              (at m Alcala)
         )
  )
```
