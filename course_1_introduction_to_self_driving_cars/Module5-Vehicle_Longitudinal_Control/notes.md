# Lesson 1: Proportional-Integral-Derivative (PID) Control
- linear or non-linear plant
-  actuators are inputs to plant, outputs are used to estimate states, states are compared with reference inputs, errors are passed to the controller
- lead-lag controllers
- PID controllers
- Zeigler-Nicols
- rise time: 90% of the reference value
- overshoot: max percentage the output exceeds the reference value
- settling time: time to settle within 5% of the reference
- steady-state error
- open loop response
- closed loop response
- open loop poles define the characteristic of the close loop response

# Lesson 2: Longitudinal Speed Control with PID
- cruise control - maintain reference speed
- ACC
- traffic jam assist - create spacing gaps
- high level controller, inputs velocity error - outputs desired acceleration
- low level controller, inputs desired acceleration - output throttle and brake
- to implement the controller we discretise it
- look at assumptions e.g. assume only throttle and no brake input
- PID tuned by trial and error

# Lesson 3: Feedforward Speed Control
- improve tracking performance particularly in dynamic manoeuvres
- feedback - closed loop
- feedforward - open loop
- feedforward - provides inputs expected to keep the plant tracking the reference (predictive response)
- feedback - corrects errors that result from disturbances or inaccuracies used by the plant model used by feedforward controller (reactive response)
- feedforward substitutes the low-level controller!!!
- feedforward can be look-up table or reference map, mapping the reference velocity to the corresponding actuator signals
- feedforward works well in steady-states
- engine map is used for the feedforward
- the PID needs errors to exist, before it can correct them. So its response lags the feedforward+PID approach
