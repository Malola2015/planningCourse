## Space Operations 

This domain models observation operations on satellites for a space company. Each satellite can have different instruments in different modes to perform observations to specific targets. 

The activities that have to be modelled are:

 - Turn (satellite, direction1, direction2): Turn the direction of a satellite from the current one to another one. It should check that the 2 directions are not equal.
 - Switch on (instrument, satellite): switch on the power of an instrument inside the satellite.
 - Switch off (instrument, satellite): switch off the power of an instrument  inside the satellite.
 - Calibrate (satellite, instrument, direction): calibrate an instrument (that should be on) inside the satellite in the direction specified.
 -  Maintenance (satellite): perform a maintenance operation.
 - Take image (satellite, direction, instrument, mode): the instrument (that should be switch on) takes an image according to a certain direction and mode. Once the image is taken, the instrument needs maintenance (two images cannot be taken sequentially). The code of this action is as follows:

 ```
  (:action take_image
   :parameters (?s - satellite ?d - direction ?i - instrument ?m - mode)
   :precondition (and (calibrated ?i)
                      (on_board ?i ?s)
                      (supports ?i ?m)
                      (power_on ?i)
                      (pointing ?s ?d)
                      (maintenance ?s))
   :effect (and (have_image ?d ?m) 
                (not (maintenance ?s))))
```

Do the following steps:

 1. Model the domain to consider types and allow equalities. 
 2. Generate a problem with the number of instruments and  satellites that you decide and the following goals:
 ```
(have_image DirPhenomenon4 Mode_thermograph0)
(have_image DirStar5 Mode_thermograph0)
(have_image DirPhenomenon6 Mode_thermograph0)
```
 3. Generate the intial state and the goal(s) whose plan is:
 ```
(turn_to satellite1 star0 phenomenon3)
(switch_on instrument1 satellite1)
(calibrate satellite1 instrument1 star0)
(perfor_maintenance satellite1)
(take_image satellite1 star0 instrument1 spectrograph2)
```
