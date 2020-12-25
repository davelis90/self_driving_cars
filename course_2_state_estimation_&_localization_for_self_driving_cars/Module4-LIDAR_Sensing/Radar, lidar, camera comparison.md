# Personal experience & internet
## Lidar:
+ good in x and y estimation (?)
- cannot see in the dark, rain, snow, fog, strong daylight
+ quite accurate
- more wobbly than radar (at least when objects are extracted)
+ if velodyne-like provides many info such as volume and more stable
- if not velodyne, no pre-processing so no objects provided (you have to extract objects)
- reflections from the ground and guard rails a problem too like radar
- lidars are bulky
- lidars are expensive
+ data has speed of light
## Radar:
+ can see in the dark, rain, snow, fog
+ good in x estimation
- not so good in y estimation
- reflections from guard rails, under the vehicle (through the road)
+ quite accurate and stable
+ many radars have many filtering options, which makes easier to get rid of false positives/reflections (Continental)
+ large range
+ easy to fit
+ same speed as lidar
- Disadvantages of RADAR Usage Shorter wavelength does not allow the detection of small objects.
## Camera (mainly with no after-sensor processing):
- cannot see so well in the dark, rain, snow, fog, strong daylight
+ detects road lines (the other sensors don't)
+ no reflections from ground or guard rails! detects only meaningful things
+ good in y estimation
- bad in x estimation - depth sensing (example of denso camera which is misclassifying the truck as a passenger cars leading to 30 m of jumps in x > useless0
+ provides many info that not all radars or lidar do still (at least the ones I've had experience with) such as classification
+ can take more info from the environment such as signs, colours
- if mobileye more stable and quite useful!
+ easy to fit
- more computationally heavy if you apply image processing algorithms
+ cameras rely more on software so a off-the-shelf camera could be enough

## Conclusion
- radar and lidar working principle is quite the same
- fusion of lidar and radar best for me
- camera (with no image processing, machine learning by us) can be used as back-up, helping in state estimation, classification
- cameras with image processing and machine learning algorithms seem to be the future though! e.g. Tesla

# Links
- https://www.autopilotreview.com/lidar-vs-cameras-self-driving-cars/#:~:text=Traditional%20radar%20uses%20radio%20waves,back%20and%20hit%20the%20car.
- https://www.viatech.com/en/2019/09/which-sensors-are-best-for-autonomous-vehicles-cameras-radar-or-lidar/
- https://www.smart-mobility-hub.com/automotive-sensor-technology-lidar-vs-radar-vs-cameras/
- https://archer-soft.com/blog/lidar-vs-radar-pros-and-cons-autonomous-driving
- https://ouster.com/blog/lidar-vs-camera-comparison-in-the-rain/

