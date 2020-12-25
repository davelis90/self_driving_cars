# Module 4: Dynamic Object Interactions
## Lesson 1: Motion Prediction
- Constact velocity prediction model
- History of vehicle states (Course 3)
- physics-based assumptions: kinematic and dynamic vehicle model
- maneuver-based assumptions (finite set of maneuvers): stay in lane unless indicating otherwise, not drive in grass/sidewalks, stop at stop signs etc
- interactions-aware assumptions: expected behaviour in a lane merge
- pedestrians have low top speed, but direction of motion changes quickly
- excellent starting point but has no context awareness: no vehicles dynamics fully, no road curvature, no road signs
- to account for the above, we use map-aware motion prediction

## Lesson 2: Map-Aware Motion Prediction
- the more constraints added to a prediction model, the less generalised will be for more driving scenarios
- with natural curvature, predicted path follow the lane center (good approximation with some deviations)
- multiple hypotheses prediction (more generic than most likely prediction) is needed e.g. in intersections
- left, right, stay stopped: evaluate the likelihood
- probabilities can be learned from training data or engineered and refined from real-world testing
- easy to adapt to human-based errors e.g. forgetting turn signal
- we can pre-process the map for nominal trajectories along each roadway - define lanelet multiple hypotheses priors
- track the evolution of beliefs over the set of hypotheseAcs and update based on the evidence from the perception stack at every time step

## Lesson 3: Time to Collision
- According to TNO and Caspar: " Inverted TTC: Relative velocity / relative distance. Standard TTC: Relative distance / relative velocity"
- TTC always treated as approximation, updated regularly and treated with some safety buffer
- Simulation approach: position, heading and occupancy extent positions are calculated at every time step (step by step approach, more comp expensive)
- Estimation approach: calculate swathe (area)/ evolution of geometry of each vehicle - check if the 2 dynamic objects will occupy the same space the same time
- Estimation approach assumptions: use object path intersection paths, use simple primitive like bounding boxes, using a constant velocity profile
- collision checking approach: i) polygon intersection ii) circle checking
- exact approach of collision: polygons
- approximation approach: circle collisions
- number of dynamic objects, the number of collisions checks changes quadratically 
- SO it makes sense to only compare the ego vehicle with other vehicles, to keep the comp complexity linear OR use a single point to point distance check between the centroids
- types for both intersection points, when the circles overlap, are provided in the suppl material
