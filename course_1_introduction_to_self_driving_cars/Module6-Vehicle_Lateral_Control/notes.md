# Lesson 1: Introduction to Lateral Vehicle Control

- ensure the vehicle can follow a pre-defined path, devised by the motion planning module
- define error relative to desired path
- take dynamic limitations and input contraints

- how to define interfaces between the Planning model and the lateral controller
- easiest: define sequence of straight line segments, very compact. Challenge: heading continuities
- refinement: tightly spaced waypoints in terms of distance or travel time, can be restricted to satisfy a curvature constraint
- continuous parameterized curves, continuously varying motion, smooths derivatives lead to consistency of error and error rate calculations
- Geometric controllers (geometry and kinematics)
- Dynamic controllers: MPC, sliding mode, feedback linearization
- heading & cross-track error
- desired heading is 0
- for straight lines, the desired rate of heading is 0
- cross-track error is an offset error

# Lesson 2: Geometric Lateral Control - Pure Pursuit

- geometric path tracking controller
- provides steering input based on a lookahead reference point
- assumes no slip in the wheels
- performance suffers when the motion of the vehicle does not satisfy the no slip condition
- in the linear tire region, it works fine
- pure pursuit uses the look ahead point on the reference path
- Stanley uses the same reference point
- pure pursuit controller does not take into account the vehicle speed! very different lateral accelerations! So we vary the look ahead distance proportionally with vehicle speed

# Lesson 3: Geometric Lateral Control - Stanley

- geometric path tracking controller also
- uses the center of the front axle as a reference point, instead of CG or the rear axle
- no lookahead distance
- obey max steering angle bounds
- independence of penalizing of heading and cross-track errors
- elimination of lookahead distance
- for small track errors, with increasing speed, the same time is needed to converge, but the car drives a bigger distance
- does not consider noisy measurements, actuator dynamics, tire force effects which lead to undesired chars in manoeuvres
- adjustment to account for such characteristics > ends up in PD controller
- add a feedforward term

# Lesson 4: Advanced Steering Control - MPC

- incorporate dynamic modelling into controller design
- solves an optimization problem at each time step
- multiple constraints
- application on linear or non-linear models
- computationally expensive
- receding horizon control algorithm 
- linear MPC is LQR!! closed form solution exists
- non-linear MPC takes all constraint as max values, no closed form solution exists - rely on numerical solutions
- reference trajectory: reference velocity, road curvature, heading angle

- MPC for double lane change maneuovre
- cost function, error, control input saturation
- constraints: models an limits
- incorporate LLC into MPC
- challenging to solve in real time
- Dynamic Window = MPC for robotics ??
