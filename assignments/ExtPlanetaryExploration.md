## Planetary exploration on Mars with time and preferences

We are going to extend the Planetary exploration on Mars domain to use time, battery and preferences. The resource to be modelled is the battery. The consumption of the battery will change according to some parameters (for example, distance or speed).

https://github.com/Malola2015/planningCourse/blob/master/assignments/PlanetaryExploration.md

From that domain, consider:  
- A new activity that extends the solar panels to recharge the battery.
- The rover can move at two speeds: fast and slow.
- Each task (from the previous domain and the new one) will have a variable duration. 

The plan will have to take into account the consumption of the battery, and when is low (defined as a threshold value) recharge the battery.

Define two preferences (don´t use them at the same time):

- ALWAYS the UGV does not move to dangerous postions (define one or two dangerous positions in your problem).

- SOMETIMES the UGV takes a picture in position x = 5 Y = 6.
