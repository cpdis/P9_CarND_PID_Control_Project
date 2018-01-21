# PID Control Project
*Self-Driving Car Engineer Nanodegree Program*

## Introduction
The purpose of this project is to control steering and throttle with a PID controler and navigate the vehicle around the track as safely as possible.

This differs from the project in Term 1 in that the vehicle has no knowledge of the world other than it's deviation from the centerline (cross track error).

## Build Instructions
1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`

## Implementation
Two controllers are used to control the steering and throttle independently.

### Parameter Tuning
The steering and throttle parameters were adjusted by trial and error until a suitable combination was found. 

#### Steering
The strategy that I adopted for steering involved initially setting the derivative (D) and integral (I) parameters to O while adjusting P. Once a suitable P parameter had been found, D was increased until the car had little to no oscillation. Adjusting I helped the vehicle make it through the several sharp turns on the course.

A few observations about how adjusting each parameter affected the motion/path of the car:

- Increasing D reduced the car's oscillation, however, if D was increased too much it caused the vehicle to lose stability through the corners by causing severe steering adjustments.

- If P is set too low it's not possible to successfully navigate the sharp turns on the course.

- If I is set to 0 then the vehicle has a bias towards the right of the lane.

#### Throttle 
The throttle controller increases or decreases the throttle based on the magnitude of the cross track error, If the CTE is high then the throttle is reduced until the vehicle is able to regain control, If the CTE is low then the vehicle is allowed to accelerate. 
