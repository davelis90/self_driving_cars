# State estimation in practise

## Lesson 1: State Estimation in Practice
-  time offsets between sensor polling times > do we do it outside of the Target Tracker?
- 1 metter accuracy requirement for highway, less for driving in dense traffic
- about 60 m in each side of the lane (lane of 3m)
- optimistic GPS accuracy is 1-5 m !!!!
- 15-30 Hz reasonable update for vehicle state

## Lesson 2: Multisensor Fusion for State Estimation
- GNSS, IMU, LIDAR use different measurement methods and are unlikely to fail for the same reason
- IMU acts a high-rate smoother of GNSS
- GNSS can mitigate error due to IMU drift
- we use GNSS and not wheel odometry, because the 2nd is limited to 2D
- LIDAR provides accurate local positioning within known maps
- GNSS tells LIDAR WHICH map to use
- IMU as input to predict (100s of times per sec)
- GNSS and LIDAR (1 per sec) as measurement
- SOS: to calculate the orientation in the measurement step we multiply the error state quartenion on the left, WHEREAS in the prediction step on the right
- SLIDE IN VIDEO IS UPDATED
- product with x means skew symmetric product!!! https://en.wikipedia.org/w/index.php?title=Skew-symmetric_matrix&oldid=977904349#Cross_product
- in slide 8 there is a mistake

## Lesson 3: Sensor Calibration - A Necessary Evil
- usually we assume delays are 0
- 2nd option is to sync with the system clock (hardware)
- 3rd is to estimate the delays

## Assignment
- https://www.coursera.org/learn/state-estimation-localization-self-driving-cars/discussions/weeks/5/threads/dfl86MD9Qka5fOjA_VJGkw
- https://www.coursera.org/learn/state-estimation-localization-self-driving-cars/discussions/weeks/5/threads/Fsv317t-EemX2AqzF6GE9g
