## Planetary exploration on Mars 

Suppose we have a rover (or several) on Mars, and we want the rover to move from an initial position to a final one. The rover can perform several tasks (not in parallel) such as:
- Move: from the origin to the source.
- Take a picture: at a given location.
- Drill: at a given location.
- Earth communication: at a given location.
- Analyse samples: at a given location.

The positions where those tasks have to be taken should be specified on the goal section using points (I would suggest you use objects to represent the X and Y coordinates, for example, X=13 Y=14 will be represented as the object P1314). The rover can perform more than one of those activities (e.g. it can take 10 pictures in 10 different positions) and while those activities are performed the rover CANNOT move. 
