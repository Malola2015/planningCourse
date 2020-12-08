We have a pizzeria that sell both, pizzas and other type of dishes that will have a different time and cooking process:
- In the pizza, the dough will be kneaded, the ingredients will be added and then, it will be baked.
- The rest of the dishes will be cooked.

These orders will be delivered on a motorcycle. For simplicity, we consider binary capacity with no fuel restrictions.

The actions in this domain are:
- kneadDough: action of kneading the dough. As a precondition the dough is not kneaded. As a postcondition, it is.  
- addTopping: action of adding topping to the dough. As a precondition the dough has to be kneaded, with no ingredients. As a postcondition, the pizza has the ingredients.
- bake: action of baking the pizza. As a precondition the dough has to be kneaded, with ingredients on top, and not baked. As a postcondition, the pizza is baked. 
- cook: action of cooking a dish. As a precondition the dish is not cooked. As a postcondition, it is.
- move: the motorcycle moves from one location to another. As a precondition the motorcycle is in the origin. As a postcondition, it is in the destination.
- load: action of loading the motorcycle. As a precondition the motorcycle is free. As a postcondition, it is loaded with the order. 
- collectOrder: action of collecting (taking the money for) the order. As a precondition the motorcycle is where the deliver is going to be performed, the money is not collected and the order is not delivered.
As a postcondition, the money is collected.
- deliverOrder: action of delivering the order. As a precondition the motorcycle is where the deliver is going to be performed, the money is collected and the order is not delivered.
As a postcondition, the order is delivered and the motorcycle is free.
 
