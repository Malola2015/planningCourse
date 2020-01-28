## Airport
The domain consists of planes and passengers that travel from one city to another. We want to model the duration of the actions and the fuel consumption. We next describe the actions:

 - Board: a person on a plane that is in a  city. As a result the person is not in the city and is on the plane. 
 - Debark: a person from an airplane. As a result the person is in the city, and is not on the plane. 
 - Fly: from one city to another. The fuel of the plane depends on the distance between the cities and the fuel ratio consumption of the plane. As a precondition, it should be verified that:
Fuel >= (distance-between-cities) x (burn-fuel-ratio of the plane)


Do the following steps:

 1. Model the previous actions and consider that all have the same duration, i.e., = 7.
 2. Add a new operator called Zoom, that consumes double but the duration = 4.
 3. Add a new action called *Refueling* that refills the tank of the plane. The tank capacity of the plane can be >= to the fuel level. Then, as an effect, the fuel level in the plane is assigned to its maximum capacity.
 4. Modify the duration of the previous actions so they are no constant but defined using predicates. 
 5. Define as a metric the fuel used:
  ```
 (:metric minimize (total-fuel-used))
  ```
 7. Define two problems. The first problem has 2 planes, 3 cities and 2 persons. And the second problem has  5 planes, 5 cities and 4 persons. As goals, all the persons should be in different positions  that the initial state. A possible initial state is:
  ```
(:init
	(in pepe4 plane2)
	(= (distance city1 city0) 1316.6534)
	(= (distance city0 city1) 1316.6534)
	(= (distance city2 city0) 1408.3523)
	(= (distance city0 city2) 1408.3523)
	(= (distance city0 city3) 2403.2266)
	(= (distance city3 city0) 2403.2266)
	(= (distance city0 city4) 2688.4637)
	(= (distance city4 city0) 2688.4637)
	(= (distance city1 city2) 1256.3465)
	(= (distance city2 city1) 1256.3465)
	(= (distance city1 city3) 1003.4996)
	(= (distance city3 city1) 1003.4996)
	(= (distance city1 city4) 986.6789)
	(= (distance city4 city1) 986.6789)
	(= (distance city2 city3) 6453.8961)
	(= (distance city3 city2) 6453.8961)
	(= (distance city2 city4) 7103.6434)
	(= (distance city4 city2) 7103.6434)
	(= (distance city3 city4) 598.6671)
	(= (distance city4 city3) 598.6671)
	(at plane2 city3)
	(= (fast-speed plane2) 10.855)
	(= (slow-speed plane2) 8.376)
	(= (capacity plane2) 913.24)
	(= (fuel plane2) 1)
	(= (fast-burn plane2) 0.5)
	(= (slow-burn plane2) 0.17)
	(= (refuel-rate pl0) 4.313)
	(at pl1 city4)
	(= (fast-speed pl1) 6.136)
	(= (slow-speed pl1) 4.795)
	(= (capacity pl1) 1477.02)
	(= (fuel pl1) 1)
	(= (fast-burn pl1) 0.809)
	(= (slow-burn pl1) 0.1)
	(= (refuel-rate pl1) 6.33)
	(at pl2 city1)
	(= (fast-speed pl2) 18.846)
	(= (slow-speed pl2) 10.075)
	(= (capacity pl2) 992.08)
	(= (fuel pl2) 1)
	(= (fast-burn pl2) 0.543)
	(= (slow-burn pl2) 0.1)
	(= (refuel-rate pl2) 13.371)
	(= (boarding-time) 30)
	(= (debarking-time) 20)
	(= (total-fuel-used) 0)
)
  ```
