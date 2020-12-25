# The Linear Kalman Filter
## Lesson 1: The (Linear) Kalman Filter
- fuse measurements from several sensors 
- prediction & correction 
- similar to recursive least squares
- use motion model derived from wheel odometry, or inertial navigation to predict
- observation model based on GPS, lidar
- input of motion model for self-driving cars should be some torque applied to speed up and change lanes
- kalman filter = recursive least squares + process (motion) model, which tells us how the state evolves over time
- uncertainty reduction occurs because the measurement model is fairly accurate

## https://www.bzarg.com/p/how-a-kalman-filter-works-in-pictures/#mathybits
- For example, if the state models the motion of a train, the train operator might push on the throttle, causing the train to accelerate. Similarly, in our robot example, the navigation software might issue a command to turn the wheels or stop. If we know this additional information about what’s going on in the world, we could stuff it into a vector called 𝐮𝑘→, do something with it, and add it to our prediction as a correction.

## Lesson 2: Kalman Filter and The Bias BLUEs
- BLUE: best linear unbiased estimator
- bias
- consistency
- unbiased estimator produces an 'average' error of zero over many trials
- for unbiased we need: i) initial state estimate is unbiased ii) noise is white (uncorrelated) and zero-mean
- inconsistent: over-confident (optimistic prediction) or underconfident (non-optimistic prediction)

# The Nonlinear Kalman Filter
## Lesson 3: Going Nonlinear - The Extended Kalman Filter
- azimuth angle (as a measurement model) changes slowly at this distance and doesn't provide much info about the vehicle state, compared to a GPS measurement (so updated covariance remains almost
the same)

## Lesson 4: An Improved EKF - The Error State Extended Kalman Filter (ES EKF)
- error state serves as a correction to the nominal state
- classical EKF, difference is: we propagate consecutive times if there no measurement (duh...) and update only if there is a measurement
- at TNO we have the vanilla EKF (only predict and update when there is a new measurement) !!!
- i) better performance than vanilla EKF ii) easy to work with constrainted quantities (rotations in 3D) - not necessary plain vector addition for the state, we can use any generalised composition operation as long as we can incorporate small perturbations to the nominal state
- evolution of the error state is close to linear (because of small time intervals between prediction steps ???)

## Lesson 5: Limitations of the EKF
- if the non-linear function varies slowly, linear approximation will be a good fit
- overconfidence of the estimator
- divergence, become completely lost
- once diverged, it can be put back on track, after re-initialisation
- linearisation error is the main problem


## Lesson 6: An Alternative to the EKF - The Unscented Kalman Filter
- unscented transform to pass probability distributions to non-linear functions
- much higher accuracy than analytical EKF-style computations (no jacobians calculated)
- approximate a probability distribution, instead of an arbitrary nonlinear function (easier)
- sigma-point transformation through a nonlinear function
