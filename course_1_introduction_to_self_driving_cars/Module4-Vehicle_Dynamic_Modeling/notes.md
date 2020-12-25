# Lesson 1: Kinematic Modeling in 2D

- at low speeds, only kinematic model sufficient
- dynamic modelling more precise throughout its entire operating range
- Inertial frame: fixed (ENU)
- Body frame: center of gravity or base link as origin
- Sensor frame
- the kinematic constraint is non holonomic, can move forward and rotate but cannot move sideways directly (velocity tangent to the path)

# Lesson 2: The Kinematic Bicycle Model

- satisfies non-holonomic constraints of a car
- front wheel steering model
- no slip condition (velocities point to the same angle as the wheel) - no movement in lateral motion and no slip in longitudinal
- center of gravity: direction of motion in cg is different (β slip angle), difference between velocity at cg and the heading at the bicycle
- velocity inputs!!

# Lesson 3: Dynamic Modeling in 2D

- take into account forces and moments!! (kinematic has velocity inputs)
- more computationally expensive
- more accurate
- we need dynamic modelling because no slip condition is not satisfied!
- expand operating range
 - split full vehicle model (3D) into 2 2D: i) steering control, ii) throttle and brake control problem

# Lesson 4: Longitudinal Vehicle Modeling

- inertial term, traction force, aerodynamic resistance, rolling resistance, gravitational force
- effective tire radius
- 

# Lesson 5: Lateral Dynamics of Bicycle Model
- tire slip angles
- relation of lateral force and slip angle
- couple differential equations

# Lesson 6: Vehicle Actuation

- steering, throttle, braking
- steering input to lateral dynamics, output is yaw rate
- throttle, braking to longitudinal dynamics, output is forward velocity
- lateral and longitudinal dynamics are separated by assumption
- linear steering system for non-aggressive driving, otherwise non-linear
- in automatic cars, gear 1 and 2 are torque modes, higher are speed modes

# Lesson 7: Tire Slip and Modeling

- slip angle, slip ratio
- tire models
- tire is the interface between the vehicle and the road
- wheels skidding, during deceleration
- wheels spinning, in low friction driving (ice)
- wheels locked, during panic breaking
- analyticalm numerical, parametrised models of tires 
- linear tire model, good approximation for the linear region, for nominal driving
- Paceijka tire model, used in model-based control
- difficulty of modelling tire forces exactly
