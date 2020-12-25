# Module 2: Mapping for Planning

## Lesson 1: Occupancy Grids
- discritised grid (2D or 3D)
- occupancy per grid location 
- each cell is a binary value
- occupancy grid corresponds ONLY to static objects, dynamic are removed
- lidar is used for making grids, ground plane, objects above the height of the vehicle and dynamic objects are filtered out
- projection onto the 2D plane
- probabilistic occupancy grid - belief map
- update beliefs in a recursive manner
- Markov assumption: all necessary info for estimating is captured at the last estimate (no earlier history is needed)

## Lesson 2: Populating Occupancy Grids from LIDAR Scan Data (Part 1)
- pc rounding error for values close to 0 leading to instability of estimates
- multiplication inneficient for small numbers
- solution: convert to logit/(log odds) function
- the final expression has the useful property of requiring addition when a new measurement is required, not multiplication
- how is the fina expression derived ????
- inverse measurement model
- Bayesian log odds update is numerically stable (logit mapping), computationally efficient (addition)


## Lesson 2: Populating Occupancy Grids from LIDAR Scan Data (Part 2)
- assumption that all lidars measurements around the vehicle are taken at the same time

## Lesson 3: Occupancy Grid Updates for Self-Driving Cars
- downsample lidar scans
- removed objects above car height
- remove lidar points hitting the ground plane/drivable surface (course 3)
- remove dynamic objects
- simplest way of downsampling: keep any nth lidar point
- other ways: image downsampling in the range image, search spatially in a 3rd grid (readily available such as pcl, openCV)
- best way to tell the ground plane is to use ground plane classification via semantic segmentation
- mapping lidar data to vision data
- more points in a cell, the greater the chance that there is a measurement of a static object in the cell

## Lesson 4: High Definition Road Maps
- data type: lanelet map
- all locations of road signs and signals
- lane boundaries are stored as a set of points creating a continuous polygonal line (polyline)
- the ordering of the points defines the heading of the lanelet
- road curvature can be pre-computed, as well as the lane center
