# Module 1: The Planning Problem

## Lesson 1: Driving Missions, Scenarios, and Behaviour
- subproblems that need to be solved for MP
- road structure scenarios
- obstacle scenarios
- depending on location and speed, different time windows of execution are available
- use estimation and prediction to calculate these windows of opportunity
- behaviours: high level manoeuvres
- edge cases make the driving tasks complex
- hierarchy of opt problems

## Lesson 2: Motion Planning Constraints
constraints:
- vehicle's kinematics & dynamics
- static & dynamic obstacles
- regulatory elements
- bicycle model imposes curvature constraint (admissible curvatures)
- curvature constraint is non-holonomic
- small curvature, large radius, "gentle bent"
- large curvature, small radius, "aggressive bent"
- friction circle (course 1?)
- static obstacles are moddeled by blocking out portions of the vehicle's workspace
- regulatory elements: signs, traffic lights, lane constraints

## Lesson 3: Objective Functions for Autonomous Driving
- objective function serves as a scoring of our MP
- path length is the total accumulated distance the car will travel, as it traverses the path
- integral of difference term (IOD)
- hinge loss term, this term is active when the velocity profile exceeds the speed limit, otherwise it's 0
- jerk is connect to the comfort of the passenger e.g. decelerating to -3 (and more) at once, is so annoying in the truck
- high curvature constrain the max velocity
- bending energy of the path = squared curvature in integral
- each of these objective functions need to be combined into 1 function e.g. weighted sum
- decouple MP problem into smaller ones

## Lesson 4: Hierarchical Motion Planning
- decompose MP problem into smaller ones: mission, behaviour, local planner sub-problems
- mission planner > map-level navigation
- behavioural planner > other agents, road rules, driving behaviours
- local planner > feasible, collision-free paths & comfortable velocity profiles
- Mission Planner: in order of km, ignore obstacles & regulatory elements and focus on: traffic and road connections, directionality
- Use graph based methods (Dijktra,A*) for shorter path
- Behaviour planner: high-level Decision Making, recognise which maneuovres are safe to take. Takes into account: pedestrians, vehicles, regulatory elements (traffic lights, stop signs)
- How does the behaviour planner take all the information and calculate which manoeuvre it should execute: i) Finite state machines (have no memory, only depend on current state) 
ii) rule-based planner (priorities are used) iii) Reinforcement learning (Beyond the scope)
- local planner - path planning part: i) sampling-based planner (RRT) ii) variational planner (cost function trajectory optimisation) > combines both path planning & velocity planning into 1 step (Beyond the scope)
iii) lattice planners (control set), Dijkstra, A*

Caspar: manoeuver planner (turn right, go straight etc), behaviour planner (more general) and Decision Making (somewhere in between, more abstract) are very similar concepts !!! 
Behaviour planner also interprets context ( I want to overtake but my sensors don't see on the right, so i'll go a bit behind or front to decided) Manoeuver planner won't do that, it will say: turn

2 big schools in MP: i) 1 trajectory generation based on behaviour planning (penalties are there), precision to the cm e.g. try to make a lane change, even if cars are passing ii) extension to take time into account (motion prediction) - trajectory generation (notion of time) - many generated trajectories sent to behaviour planning to choose the least penalised one e.g. take cars into account before starting the lane change, right in the middle of the lane iii) path planning (no notion of time) leading to trajectory generation (TNO way) iv) corner case is AES (hybrid)
