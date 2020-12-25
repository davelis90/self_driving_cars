# Module 5: Principles of Behaviour Planning
## Lesson 1: Behaviour Planning
- construct behaviour planner through a (finite) state machine
- take into account: road rules, static objects, dynamic objects
- example: where and when to stop, how long to stay stopped for and when to proceed through the intersection
- should also be able to deal with correct and incorrect perception inputs !!!! INTERESTING
- basic driving behaviours - likely maneuvers: look at ppt
- in the output are constraints, used for the local planner, 1 of these is: set of interest vehicles (MIOs)
- with all the necessary inputs, the behaviour planner must choose the appropriate behaviour and define the necessary constraints 
- each state is associated with an entry action (decelerate to stop)
- as the number of scenarios increases, the state machine becomes more complex
- only relevant transitions out of the current state need to be considered, reducing the number of conditions to check
- clear divisions between separate behaviours
- no explicit way to handel uncertainties and errors in the input data > run into difficulties as we approach Level 5, but excellent start for restricted ODD systems
- that's why there are alternatives > last video of module

## Lesson 2: Handling an Intersection Scenario Without Dynamic Objects
- we start adding more capabilities to the finite state machine behaviour planner
- state entry action for track speed: sets the speed limit
- entry action for decelerate to stop: stop point location (stop sign by HD map)
- entry action for track stop: start a timer to wait for a fixed amount of time before proceeding
- scenario and specific capabilities of the resulting behaviour planner > need to be captured in the ODD and we need to define a complete state machine for every possible case for the given scenarios
- handle input noise by setting thresholds
- simulation tests confirm if the state machine transitions and state coverage are correct, to catch any edge cases
- private track tests: parameter tuning, noise and errors in the perception algorithm
- road tests can be highly unpredictable, new variations of scenarios can be entered into earlier stages of the testing process

## Lesson 3: Handling an Intersection Scenario with Dynamic Objects
- measurement of the distance to various interaction points with the other objects
- Track Speed to Follow Leader - follow check: i) distance check ii) same lane check
- check if lead vehicle is i) in the lane limits ii) heading of dynamic object is within a given threshold w.r.t the ego vehicle (same direction) - DynObj.TTC >= followThreshold Shouldn't it be reversed ???
- During Stop, we adopt a conservative driving style - waiting till all vehicles have cleared the Approaching, At or On intersection zones
- -45 to 45 degrees dynamic objects goes in the same heading as the ego vehicle, -45 to -135 right, -135 to 135 towards the ego vehicle, 45 and 135 left
- when a vehcile wants to go left, any vehicle from left, right or straight should clear the zones
- when straight, only left or right should clear the intersection
- when right, only left. Follow leader could occur here.
- the fact that dynamic obstacles don't alway obey the rules, leads to edge cases
- edge cases: unintentional swerve into oncoming traffic, aggressive driver racing through an intersection when the ego vehicle is already in, vehicle fails to stops, parked vehicle in close proximity to the intersection which is NOT labelled as parked > planner stuck in deadlock
- we should also define how the vehicle should react to edge cases > emergency maneuvers: swerve (AES in TNO = Advanced Evasive Steering ?), hard breaker

## Lesson 4: Handling Multiple Scenarios
- hierarchical finite state machine
- each scenario requires fundamentally different driving behaviours
- 1 method: add additional states in a single state machine
- 2 method: multiple state machine, represent each high level scenario as a single state (superstate) e.g. intersection scenario, drive-lane scenario
- superstates represent each scenario, sub states represent the maneuvers in each scenario
- distance check to the next intersection along the mission plan
- define in which states of each scenario, exit transitions can be added
- condition if each scenario is complemeted e.g. check distance to next stop sign intersection
- multiple lane scenario
- multiple layers as long as key states can be defined at each level
- the idea that 1 single behaviour is active at any time and that all transitions can be explicitely defined has a limit in the number of scenarios that it can handle

## Lesson 5: Advanced Methods for Behaviour Planning
- developing a full level 4 or 5 is almost impossible with finite state machines due to rule explosion
- fuzzy logic: continuous space . Rule explosion and hyparameter tuning are still problems. , fuzzy logic systems are more robust to environmental noise than traditional discrete systems, such as a finite state machine.
- reinforcement learning: by maximising the reward, the agent eventually learns to master the task
- In simulation, no real-world failures occur during learning.
- learn a policy which maps an environment state to an action
- each low level policy is learned independently and only when learned, the high level policy is learned
- a model-based RL example would be to include a model of the movement of dynamic objects
- overly realistic simulators lead to the issue of severe computational requirements
- black boxes of decision lead to lack of safety insurance, the policies learned by reinforcement learning are often not human-interpretable
- Behaviour planning remains a hot bed in ADAS and toughest bottlenecks to achieve real level 5 !!!!
