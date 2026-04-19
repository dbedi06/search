Q1 - Depth-First Search:
I don't think that DFS finds the least-cost solution. It found a path length of 130 on mediumMaze, which is not optimal. It explores deep paths first based on stack order, not path cost. Pacman only travels the found path, not every explored node.

Q2 - Breadth-First Search:
BFS pretty much finds a least-cost solution when all step costs are equal. It found the optimal path of length 68 on mediumMaze by expanding nodes layer by layer.

Q3 - Uniform Cost Search:
My UCS apporoach generalizes BFS by using a priority queue ordered by cumulative cost. It handles varying step costs correctly, which is why it finds different path lengths (68, 74, 152) depending on the cost function used.

Q4 - A\* Search:
A* expanded only 221 nodes on mediumMaze compared to BSF's 269, because the Manhattan heuristic guides it toward the goal. On openMaze, A* shows an even larger advantage since the open space gives the heuristic more room to prune unnecessary exploration.

Q5 - Corners Problem:
The state is (position, visitedCorners) where visitedCorners is a tuple of four booleans. This encodes exactly the information needed to detect completion, no irrelvant game state. BFS on this found the optimal 28-step solution for tinyCorners.

Q6 - Corners Heuristic:
The heuristic greedily estimates the cost to visit all remaining corners using Manhattan distance, always picking the nearest unvisited corner next. It's admissible since Manhattan distance never overestimates real maze cost. It expanded only 692 nodes and found the optimal 106-step path.

Q7 - Food Heuristic:
The heuristic is the maze distance to the farthest remaining food dot, you must travel at least that far regardless of eating order, making it an admissable lower bound. Distances are cached to avoid recomputation. This expanded only 4137 nodes on trickySearch, earning the optional extra credit.

Q8 - Closest Dot Search Agent:
AnyFoodSearchProblem uses self.food[x][y] as the goal test, and findPathToClosestDot runs BFS on it since BFS guarantees the shortest path to the nearest food. This agent won't always find the globally optimal route. For example, two dots at opposite ends of a corridor with one nearby in the middle could cause unnecessary backtracking.
