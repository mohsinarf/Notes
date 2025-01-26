# Dijkstra Algorithm
Dijkstra's algorithm is a widely used algorithm for finding the shortest paths between nodes in a weighted graph, which can represent things like road networks.

The algorithm works as follows:
1) It starts with a source node and initializes the distance to that node as 0, and the distances to all other nodes as infinity (or a very large number).
2) It then repeatedly selects the unvisited node with the smallest distance from the source, and updates the distances to that node's neighbors. If the sum of the distance to the current node and the weight of the edge to a neighbor is less than the neighbor's current distance, the neighbor's distance is updated.
3) Once a node is selected, it is marked as visited and will not be considered again.
4) The algorithm continues this process until all nodes have been visited. At this point, it has calculated the shortest distance from the source node to every other node in the graph.
5) To reconstruct the actual shortest paths, the algorithm keeps track of the "previous" node in the shortest path for each node. This allows the full path to be traced back from any node to the source.

Some key properties of Dijkstra's algorithm:
- It is a greedy algorithm, always choosing the nearest unvisited node to expand the path.
- It requires the graph to have non-negative edge weights, unlike the Bellman-Ford algorithm which can handle negative weights.
- It has a time complexity of O(E + V log V), where E is the number of edges and V is the number of vertices in the graph.
- It is commonly used in routing protocols like OSPF and IS-IS, as well as in applications like Google Maps to find optimal routes

## Reference
https://www.youtube.com/watch?v=bZkzH5x0SKU&ab_channel=FelixTechTips

