# Module 7: Putting it all together - Smooth Local Planning
## Lesson 1: Parametric Curves
- result of local planner is either a trajectory (sequence of points in space at given times), or a path & velocity profile (sequence of points in space with the required velocities at each point) - this can be the input to the controllers developed in course 1
- position (x,y), heading(θ) and curvature(κ) of start and end goal
- boundary conditions should hold on either endpoint of path - for us the only kinematic constraint is the max curvature along the path ONLY
- take sample points along the path
- optimise a given path based on boundary conditions, kinematic constraints and an objective function
- in module 6 we created a non-parametric path
- quintic splines AND cubic spirals are used commonly in automotive as parameterised curves
- quintic splines: 12 parameters (for x and y), u=0 start of the path - u=1 end
- challenging to constraing curvature with quintic splines
- polynomial spirals are defined by their curvature as a function of arc length
- splines has closed form solution, whereas the spiral does not
- spirals ensures smooth curvature variation across the path, whereas the splines does not
- spline leads to comp efficiency, spiral to easier implementation of curvature constraints
- WE WILL USE SPIRAL HERE!

## Lesson 2: Path Planning Optimization
- constraints (curvature for us) & parametrised curves combination > smooth feasible paths
- spiral end position requires numerical approximation (integration technique such as Simpson's rule)
- Simpson's rule evaluates the integral of the quadratic interpolation so more accurate
- as n increases, accuracy increases
- bending energy objective function
- we define the vehicle planning problem in the vehicle frame

## Lesson 3: Optimization in Python

## Lesson 4: Conformal Lattice Planning
- feasible collision-free path to goal
- first compute kinematically feasible spirals
- second check collision-free
- use trapezoidal rule (linear) instead of Simpson's rule, since more efficient
- then compute collision-free paths
- then select the best path (with an objective function > design choice)
- the penalty should increase the further we get from the center goal e.g. displacement from center goal
- follow reference path and deviate only if it is infeasible or collides with an obstacle

## Lesson 5: Velocity Profile Generation
- many different factors that affect the velocity profile: reference velocities from behaviour planner, leading vehicle TTC and comfort constraints
- linear ramp OR trapezodial velocity profile
- calculate all curvatures (in case it changes rapidly, lat accelration would be big), find the associasted max speed for that point > make sure that our velocity profile matches that specific speed

## Final Project Overview
- spiral optimisation to generate paths
- circle-based collision checking method for static obstacles
- generate velocity profiles that avoid dynamic obstacles
- develop a state machine for behavioural planning for a stop sign scenario
