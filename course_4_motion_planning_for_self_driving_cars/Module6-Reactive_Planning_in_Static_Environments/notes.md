# Module 6: Reactive Planning in Static Environments
## Lesson 1: Trajectory Propagation
- kinematic models take velocities as inputs
- dynamic models take forces and torques as inputs
- often we don't have direct access to the robot state (x,y, theta) BUT we can device a sequence of control inputs to lead the state where we want
- discretisation of kinematic model > simple ZOH is presented
- with discretisation we get an accurate approximation of the robot trajectory > used for motion prediction & trajectory planning


## Lesson 2: Collision Checking
- must be ROBUST TO NOISE (we should add buffers to collision checking algorithms to make them more error-tolerant)
- swath = trail, strip
- occupancy grid resolution 1 m
- order of steps matters: first rotation, then translation
- X, Y are x and y dimensions of the occupancy grid
- store associated indices in a set (ensuring no duplicates)
- expensive computation, difficult to use for Real-time planning
- calculating swath could be dangerous due to imperfect info - no buffer for errors
- swath based methods are good for a lot of repetition in the MP algorithm e.g. lattice planners
- conservative approximations > use 3 circles to encapsulate car - footprint of car (and footpring of swath) is a subset of the footprint of all 3 circles combined
- conservatice collision checker will contain false positives but NOT false negatives > nice buffer to aleviate issues provided by imperfect info
- conservative approx may eliminate all feasible collision-free paths, even though 1 exists. Or eliminate safe passages through narrow openings
- which collision check algorithm to use depends on MP algorithm and occupancy grid structure (up to the engineer to choose)
- resolution of discretisation should be chosen as well to balance accuracy and computational speed (avoid gaps in swaths as shown is 2nd to last slide)
- many collision checking libraries available
- active research in collision checking, especially with dynamic objects
- why is collision checking computationally challenging in exact form? i) requires perfect info ii) heavy geometric computations in continuous domain iii) problem scales with number of obstacles in a given space

## Lesson 3: Trajectory Rollout Algorithm
- this is JUST 1 algorithm of Reactive Planner !!!
- reactive planning algorithm of this module > trajectory rollout algorithm = combines collision checking and trajectory propagation concepts
- intro to the trajectory planning task, more advanced methods in module 7
- maximise an objective function, that include a term which rewards progress towards the goal
- generate set of trajectories at each time step
- check with trajectories are collision-free: we are given an occ grid (discretisation), stored in a matrix where each value denotes if occupied or not
- perform collision checking with swaths (sweeping body of robot along the path), footprint corresponds to a set of indices (in the occupancy grid) - check each point of the swath to see which overlap
 with obstacles in the occupancy grid
- if ANY point is occupied then that trajectory contains a collision
- after filtering, we are left with a set of collision-free trajectories, which we score based on the objective function: min distance from trajectory end to goal > we greedily search for the goal region
- no perfect objective function, we can use many criteria e.g. reward maximising distance to obstacles
- receding horizon planner: execute portion of selected trajectory (1 sec out of 2 sec prediction)
- greedy planner, can be short-sighted, get stuck to dead ends (because it is a receding-horizon planner), find sub-optimal paths and locally optimal solutions (myopic)
- dynamic windowing helps trajectory rollout algorithm to produce more comfortable trajectories
- swath is the space the car occupies along the path


## Lesson 4: Dynamic Windowing
- augment trajectory rollout algorithm with dynamic windowing, which allows to place linear and angular acceleration constraints to promote comfort 
- lose maneuverability
