# Lesson 1 (Part 1): Squared Error Criterion and the Method of Least Squares

## Ordinary least squares
- localisation is the method of determining the position and orientation of the vehicle
- state estimation vs parameter estimation (constant over time)
- squared error criterion = squared error cost or loss function 
- measurement model
- number of measurements should be >= unknown parameters to have a unique solution
- assumptions: linear model, equally weighted measurements

# Lesson 1 (Part 2): Squared Error Criterion and the Method of Least Squares

## Weighted least squares
- weight least squares can account for measurements of varying importance (different quality)
- higher expected noise > lower measurement weight
- derivative of many variables becomes a gradient

# Lesson 2: Recursive Least Squares

- batch solution (previous methods) assume that we have all the measurements at once
- what if we have a stream of data? we need a recursive method > linear recursive estimator
- recursive least squares criterion
- Initialise estimator: mean comes from the first measurement and covariance comes from tech specs
- RLS produces a running estimate of parameters for a stream of measurements, not a batch
- RLS is like a kalman filter with no prediction step (MY OWN EXPLANATION)

# Lesson 3: Least Squares and the Method of Maximum Likelihood
- why squared errors? i) relative straightforward algebra ii) probability, connection between max likelihood estimators and least squares
- which value would maximise the conditional likelihood, given the measurement y_meas?
- maximal likelihood estimate (MLE)
- Central Limit Theorem
- poor measumerements (outliers) have a significant effect on the method of least squares, skewing the mean value so that the outlier is more probable e.g. person walking in the middle of the lidar scan
or a bad GPS signal
- we always should try to quantify the error distribution before blindly applying least squares
