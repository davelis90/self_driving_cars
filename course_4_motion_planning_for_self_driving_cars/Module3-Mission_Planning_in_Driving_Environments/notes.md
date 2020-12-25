# Module 3: Mission Planning in Driving Environments

## Lesson 1: Creating a Road Network Graph
-  objective: find optimal path from current position to given destination while abstracing lower level info such as rules of the road and other agents
- optimality w.r.t. time and distance
- order of km
- mission planner focuses on aspects of the road network e.g. speed limits, road lengths, traffic flow rates and road closures
- optimal path based on the map given to us
- road needs to be discreetly sampled
- many cases there is 1 directions between 2 vertices
- graph-search algorithm - Breadth first search (BFS)
- open queue still to be assessed
- closed queue that have been assessed
- predecessors store the results of the search
- a queue is used for its first-in, first-out (FIFO) property that ensures we process adjacent vertices before proceeding deeper in the graph.
- we do not add a already added vertex to the queue (original predecessor remains)
- Depth first search algorithm: inverse of breadth first search algorithm - backtracking the vertices
- Breadthfirst assumes that all road segments have equal length!!! Does not take edge weights into consideration

## Lesson 2: Dijkstra's Shortest Path Search
- adding weights to a graph better reflects the autonomous driving mission, as different roads are longer than others
- many parameters an affect the costs, here we will focus purely on distance > using edge weights ( e.g. number of km)
- min heap: stores keys in values, sorts the keys in terms of their values, smallest to largest (distance to reach that vertex along the shortest path)
- processing vertices in the order formed by the min heap in Dijkstra's algorithm ensures that we process the vertices that are closest to the origin first.
- update costs in already included paths if cheaper
- what is the main purpose of keeping track of a "closed" set of graph vertices? To avoid getting stuck in cycles. By keeping track of which vertices we have already processed, we can avoid re-searching another vertex if the graph contains cycles.

## Lesson 3: A* Shortest Path Search
- involves search heuristics to refine the search process
- potentially faster approach
- Dijkstra searches all edges in the graph, not efficient
- vertex costs are based on absolute distance, edge costs are based on actual road length (curves, turns, not straight line paths)
- the heuristic estimate must always be an underestimate of the actual cost,  if the heuristic estimate is larger than the true cost, then the heuristic is not admissible.
- A* biases the search towards vertices that are likely to be part of the path
- if h(v) = 0, we end up with Dijkstra
- asymptotically, A* will never do worse than Dijkstra
- time is better than distance to replace edge weights (takes other factors in consideration)
- more advance methods pre-compute additional values for modified heuristics definitions (with time-based travel estimates road networks)

## Assignment
- OSMnx is a Python package that lets you download spatial geometries and model, project, visualize, and analyze real-world street networks from OpenStreetMap’s APIs: https://osmnx.readthedocs.io/en/stable/
- https://networkx.org/documentation/stable/
