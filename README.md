# AI-Mini-Project
Design and implement an efficient algorithm to find the shortest path between two cities on a map of Maharashtra, India, using the A* search algorithm. The algorithm should generate the heuristic value dynamically for each city pair using the Haversine and Vincenty formulas, taking into account the geographical coordinates of the cities.
2.2	Explanation of code

The code provided implements the A* (A-star) algorithm for finding the shortest path between two nodes in a graph. The algorithm uses a heuristic function to guide the search towards the goal node efficiently. Here's a breakdown of the code:


1.	The code begins by defining an empty dictionary `H_dist` and a function
`aStarAlgo` that takes two parameters: `start_node` and `stop_node`.



2.	Inside the `aStarAlgo` function, several variables are initialized: `open_set` (a set to store nodes that are yet to be evaluated), `closed_set` (a set to store nodes that have been evaluated), `g` (a dictionary to store the distance from the starting node), and `parents` (a dictionary to store the parent of each node).


3.	The algorithm starts by setting the distance of the `start_node` from itself to 0 and adding it as its own parent.


4.	The algorithm enters a loop that continues until the `open_set` is empty. Within the loop, it selects the node `n` with the lowest "f" value (the sum of the distance from the starting node `g` and the heuristic value `heuristic`) from the `open_set`.


5.	If the selected node `n` is equal to the `stop_node` or there are no neighbors for
`n` (Graph_nodes[n] is None), the loop is terminated. 
6.	If `n` is not the `stop_node` and it has neighbors, the algorithm iterates over each neighbor `(m, weight)` obtained from the `get_neighbors` function.


7.	If the neighbor `m` is not in the `open_set` and `closed_set`, it is added to the
`open_set`, and its `g` value is updated as the sum of the `g` value of `n` and the weight of the edge between `n` and `m`. The parent of `m` is set to `n`.


8.	If the neighbor `m` is already in the `open_set` or `closed_set`, the algorithm checks if the new path through `n` has a lower `g` value. If so, the `g` value of `m` is updated, its parent is changed to `n`, and if `m` is in the `closed_set`, it is removed from it and added back to the `open_set`.


9.	After processing all neighbors of `n`, it is removed from the `open_set` and added to the `closed_set`.


10.	If the loop terminates without finding the `stop_node`, it means there is no path, and the function returns `None`.


11.	If a path is found, the algorithm reconstructs the path from the `start_node` to
`n` using the `parents` dictionary and appends each node to the `path` list.



12.	Finally, the `path` is reversed and printed, and then it is returned by the function. 


The code also includes additional functions:



-	`get_neighbors(v)`: Returns the neighbors and their distances for a given node `v` based on the `Graph_nodes` dictionary.


-	`calculate_heuristic(start, goal)`: Calculates the heuristic value (straight-line distance) between two coordinates using the Haversine formula. This formula takes into account the Earth's radius and the latitude and longitude coordinates of the start and goal points.


-	`calculate_heuristics(cities, goal)`: Calculates the heuristic values for multiple cities based on a goal city. It iterates over each city, calculates the heuristic value using the `calculate_heuristic` function, and stores the result in a dictionary.


-	`heuristic(n)`: Returns the heuristic 
