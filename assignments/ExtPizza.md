## Pizzeria with time, capacity and preferences

Extend the Pizza domain to use durations, take into account the capacity of the motorcycle in the orders and the fuel consumption. 

https://github.com/Malola2015/planningCourse/blob/master/assignments/Pizza.md

Consider the following partial problem definition and adjust the domain extending and/or deleting/adding operators.
 
```
(:objects 
    pizzeria - local
    repsol - gasStation
    casa1 casa2  - house
    lasagna macarrones - dish
    pizza1 - pizza
    vespa - moto
)

(:init

    (= (cantidad_gasolina vespa) 180) ; in liters 
    (= (gasolina_requerida pizzeria casa1) 20) ; in liters
    (= (gasolina_requerida pizzeria casa2) 25)
    ...
   
    (= (distancia pizzeria casa1) 2) ; in kms
    (= (distancia pizzeria casa2) 3)
    ...
    

    (= (dur_Knead) 3) ; in min
    (= (dur_addTop) 1) ; in min
    (= (dur_cook lasagna) 40) ; in min
    (= (dur_cook macarrones) 35) ; in min
    (= (dur_bake) 15) ; in min
    (= (dur_collect) 1) ; in min
    (= (dur_deliver) 1) ; in min
    ...
    
    (= (velocidad vespa) 35) ; in km/h 
    ...    
    (= (umbral_gasolina) 20) ; refuel the motorcycle when the tank has a capacity of 20 liters or below

    (at pizzeria vespa) 

    (= (capacidad_moto vespa) 3) 
    (= (carga_actual vespa) 0) 

)
(:goal 
(and
    (entregado pizza1 casa1) 
    ...
))

(:metric minimize (total-time)) 
)
```
