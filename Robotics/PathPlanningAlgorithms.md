| Algorithm                | Description                                                                            | Pros                                                                       | Cons                                                                   | Space Complexity | Time Complexity                  |
|--------------------------|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------|------------------------------------------------------------------------|------------------|----------------------------------|
| Depth-First Search (DFS) | Explores as far as possible along each branch before backtracking.                      | - Requires less memory than BFS.                                           | - Does not guarantee the shortest path.                               | O(bd)            | O(b^m) in the worst case         |
|                          |                                                                                        | - May find a solution faster than BFS in some cases.                       | - Can get stuck in infinite loops if not implemented carefully.         |                  |                                  |
|                          |                                                                                        | - Useful for unweighted graphs or when the shortest path is not required.   |                                                                        |                  |                                  |
| Breadth-First Search     | Explores neighbors before children, traversing the graph level by level.               | - Guarantees the shortest path.                                            | - Requires more memory than DFS.                                      | O(b^d)           | O(b^d)                           |
| (BFS)                    |                                                                                        | - Ideal for finding the shortest path in unweighted graphs.                | - May be slower than DFS in some cases.                              |                  |                                  |
|                          |                                                                                        | - Suitable for scenarios where finding the shortest path is crucial.       |                                                                        |                  |                                  |
| Dijkstra's Algorithm     | Finds the shortest path from a single source node to all other nodes in a weighted graph with non-negative edge weights. | - Guarantees finding the shortest path from the source node to all other nodes. | - Does not work with negative edge weights.                           | O(V) + O(E)      | O((V + E) * log(V)) for binary heap |
|                          |                                                                                        | - Well-suited for weighted graphs with non-negative edge weights.          | - Requires more computational resources compared to DFS and BFS.        |                  |                                  |
| A* Algorithm             | A combination of Dijkstra's algorithm and a heuristic function, guiding the search by prioritizing nodes closer to the goal. | - Optimal if the heuristic is admissible and consistent.                    | - Requires an accurate heuristic function.                           | O(V)             | O(b^d) where d is the solution depth |
|                          |                                                                                        | - Ideal for finding the shortest path in weighted graphs with a heuristic.  | - More complex to implement compared to DFS and BFS.                   |                  |                                  |


Depth-First Search (DFS), Breadth-First Search (BFS), Dijkstra's algorithm, and A* algorithm are all graph traversal algorithms used for path finding, but they differ in their approach and suitability for different scenarios.
## DFS (Depth-First Search)
DFS explores as far as possible along each branch before backtracking. It is suitable for finding any path between two nodes, but not necessarily the shortest path. It has a time complexity of O(V+E), where V is the number of vertices and E is the number of edges.
## BFS (Breadth-First Search)
BFS explores all vertices at the current depth before moving on to vertices at the next level. It is suitable for finding the shortest path between two nodes in an unweighted graph. It has a time complexity of O(V+E), where V is the number of vertices and E is the number of edges.
## Dijkstra's Algorithm
Dijkstra's algorithm is used to find the shortest path between a source node and all other nodes in a weighted graph. It works by maintaining a set of visited nodes and a priority queue of unvisited nodes, prioritizing nodes with the shortest distance from the source. It has a time complexity of O((V+E) log V), where V is the number of vertices and E is the number of edges.
## A* Algorithm
A* is an informed search algorithm that combines features of Dijkstra's algorithm and greedy best-first search. It uses a heuristic function to estimate the cost from the current node to the goal node, allowing it to find the shortest path more efficiently than Dijkstra's algorithm in many cases. Its time complexity can vary depending on the heuristic used and the structure of the graph.
In summary, for finding the shortest path in an unweighted graph, BFS is the most suitable algorithm. For weighted graphs, Dijkstra's algorithm is the standard choice. A* can be more efficient than Dijkstra's algorithm in certain cases, but it requires a good heuristic function. DFS is useful for finding any path between two nodes, but not necessarily the shortest path.


Rapidly-exploring Random Trees (RRT)
Probabilistic Roadmap (PRM)
Wavefront algorithm
D* Lite
A* algorithm
