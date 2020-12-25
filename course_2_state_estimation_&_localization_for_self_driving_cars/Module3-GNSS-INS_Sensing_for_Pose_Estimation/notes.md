# GNSS/INS Sensing for pose estimation
## Lesson 1: 3D Geometry and Reference Frames
- vector has magnitude and a direction
- base coordinate frame
- why use quaternions? they don't suffer from singularities and they need only 4 instead of 9 parameters (as in the rotation matrix of a 3-D)
- in quartenion multiplication, the order of multiplication matters!
- Euler angles have 3 dimensions instead of 9, BUT they suffer from singularities: particular rotations where 2 Euler angles are indistinguisable
- for car applications, we need a fixed reference frame fixed to the ground
- ENU frame equal to utm???
- Z faces down in NED and sensor and vehicle frame!!! (same as Matlab automotive?)

## Lesson 2: The Inertial Measurement Unit (IMU)
- 2 basic components: accelerometer and a gyroscope
- gyroscope > measure angular rotation rates (velocities) about 3 axes
- accelerometer > measure linear accelerations along 3 axes
- some IMUs contain magnetometers or compass to provide heading/orientation
- movement of a body in an inertial picture
- MEMS substitute the gyroscope
- accelerometers measure non gravitational (specific) force or proper acceleration e.g. normal force alone, without gravitational force
- in a stationary car f = -g (upwards)
- for the accelerometer we need to remove the gravitational acceleration
- Earth's rotation is important for long distance navigation
- 6-DOF is composed of 3 gyroscopes and 3 accelerometers, mounted orthogonally
- since strapdown IMUs are tricky to calibrate and drift over time, **we need the GNSS to correct our pose estimates**
- dead reckoning is when GPS is down and we rely on IMU!!!
- A major disadvantage of using IMUs for navigation is that they typically suffer from **accumulated error**. Because the guidance system is continually integrating acceleration with respect to time to calculate velocity and position (see dead reckoning), **any measurement errors, however small, are accumulated over time**. This leads to '**drift**': an ever-increasing difference between where the system thinks it is located and the actual location. Due to integration a constant error in acceleration results in a linear error in velocity and a quadratic error growth in position. A constant error in attitude rate (gyro) results in a quadratic error in velocity and a cubic error growth in position.[15]

Positional tracking systems like GPS [16] can be used to continually correct drift errors (an application of the Kalman filter).
- gyro integration aka dead reckoning accurate in short term, but not reliable in long term due to drift - remove with high pass filter
- accelerometer unreliable in short run due to motion (and noise) - remove noise with low-pass filter
- magnetometer > complementary to accelerometer – gives yaw (heading)
- read **lecture9.pdf**

## Lesson 3: The Global Navigation Satellite Systems (GNSS)
- provides a position fix anywhere in the world with bounded error!
- at least 4 satellites are visible at any surface point at all times > 4 needed to compute a 3D position plus receiver clock error, 3 if only 2D is required (plus receiver clock error)
- if we have more than 4 we can use least squares to find the max likelihood position, assuming Gaussian noise
- GPS signals: satellite position + time of signal transmission
- one small time error can lead to 10ths of meters position error
- guaranteed level of position accuracy-bounded error UNLIKE IMU
- GPS > American, Galileo > EU, Glonass > USSR, Compass > China
