# Sampling-Based Algorithms

### Random Tree

Random Tree is a simpler variant of RRT where there's no bias towards expanding the tree towards the goal. Instead, nodes are added randomly, resulting in a tree structure that explores the configuration space without a specific goal-driven strategy.

#### Algorithm Steps:

1. **Initialization**: Same as RRT.
2. **Expansion**: Repeat until a specified number of iterations is reached.
   - Randomly sample a state in the configuration space.
   - Extend the tree towards the sampled state by choosing the nearest state already in the tree and creating a new node towards the sampled state.
   - Ensure the new node is collision-free.
3. **Path Construction**: Not applicable in standard Random Tree as there's no specific goal.
4. **Output**: The final tree structure after the specified number of iterations.

#### Pros:
- Simplicity in implementation.
- Can be used for exploration tasks without a specific goal.
- Provides a structure for further analysis of the configuration space.

#### Cons:
- Lacks a specific goal-directed strategy.
- May not efficiently find paths in goal-directed tasks compared to RRT and RRT*.

### RRT (Rapidly-exploring Random Tree)

RRT is a probabilistically complete motion planning algorithm used in robotics for path planning in high-dimensional spaces. It aims to efficiently explore the configuration space by incrementally building a tree of sampled states.

#### Algorithm Steps:

1. **Initialization**: Start with a tree consisting of only the initial state.
2. **Expansion**: Repeat until a goal state is reached or a specified number of iterations is achieved.
   - Randomly sample a state in the configuration space.
   - Extend the tree towards the sampled state by choosing the nearest state already in the tree and creating a new node towards the sampled state.
   - Ensure the new node is collision-free.
3. **Path Construction**: If the goal state is reached within the specified number of iterations, construct a path from the initial state to the goal state by backtracking through the tree.
4. **Output**: Return the path if found, else return failure.

#### Pros:
- Simple to implement.
- Efficient in high-dimensional spaces.
- Probabilistically complete (finds a solution if one exists given enough iterations).

#### Cons:
- May not find the optimal path.
- Path quality highly dependent on the number of iterations and the sampling strategy.
- Sensitivity to choice of parameters.

### RRT* (RRT Star)

RRT* is an extension of the RRT algorithm that addresses some of its limitations, aiming to find optimal paths more efficiently by gradually improving the tree structure.

#### Algorithm Steps:

1. **Initialization**: Same as RRT.
2. **Expansion**: Same as RRT.
3. **Rewiring**: After adding a new node, check if any nearby nodes can be reached more efficiently through the new node. If so, rewire the tree to use the new node, improving path quality.
4. **Path Construction**: Same as RRT.
5. **Output**: Same as RRT.

#### Pros:
- Finds near-optimal paths more efficiently compared to RRT.
- Less sensitive to parameters due to the rewiring step.
- Probabilistically asymptotically optimal.

#### Cons:
- Slightly more complex implementation compared to RRT.
- Still not guaranteed to find the optimal path in finite time.



