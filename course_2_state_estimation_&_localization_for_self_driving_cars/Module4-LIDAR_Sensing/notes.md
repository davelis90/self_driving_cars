# LIDAR sensing

## Lesson 1: Light Detection and Ranging Sensors
- Lidar provides 3D scans of the environment
- measure distances to a single point, a 2-D slice of the world or a full 3-D scan
- components: laser, photodetector and very precise stopwatch
- emits a short pulse of light (speed of light), stopwatch begins counting, unless the surface is not too shiny the pulse will scatter off, some of that will travel back to the photodetector,
stopwatch tells you how much time has passed (roundtrip time) > calculate distance - time-of-flight ranging (same as radar, sonar)
- photodetector also tells you the intensity of the received pulse, which provides info about geometry of environment and material of target
- with LIDAR we can see in the **dark**!
- for velodyne type of lidars, multiple 2-D scan lines are created and are combined
- in a lidar scans, each point is coloured by the intesity of the return signal
- entire collection of points in 3-D scan is called pointcloud
- motion distortion is a problem, since each point in a scan is taken from a different place of the ego vehicle > can lead to duplicate objects

## Lesson 2: LIDAR Sensor Models and Point Clouds
- lidars pointclouds to contain up to 1 million points
- for state estimation, objects stay put and the reference frame (ego frame) moves through the world
- plane fitting
- Python: solve linear system numpy.solve
- pcl in c++ (point cloud library)
- Iterative closest point (ICP) algorithm, used to estimation ego motion using 2 lidar pointclouds
- A point cloud is a data structure used to represent a collection of multi-dimensional points and is commonly used to represent three-dimensional data. In a 3D point cloud, the points usually represent the X, Y, and Z geometric coordinates of an underlying sampled surface. When color information is present (see the figures below), the point cloud becomes 4D.

## Lesson 3: Pose Estimation from LIDAR Data
- point set registration 
- feature matching (computer vision) is a way of determinging correspondence between points, using camera data
- we need a good starting guess, so that we don't get stuck in local minima
- 1 point in 1 cloud can be associated to 2 points in another cloud (same cloud moving in time)
- rotations need special treatment, they don't behave like vectors e.g. adding 2 rotation matrices does not necessarily provide a rotation matrix
- ICP alone can be misleading e.g. if the object and the ego vehicle move at similar speed in the same direction - we need stationary objects
