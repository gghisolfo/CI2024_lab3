# N-puzzle problem
N-Puzzle supports five different Graph-based Search Algorithms. 

The first three are **Uninformed Search Algorithms**:

-   Breadth-first Search
-   Depth-first Search
-   Iterative Deepening Search

The other two are **Informed Search Algorithms**:

-   A* Search
-   Greedy Search

If you choose an Informed Search Algorithm, then you will also need to select a Heuristic Function.

# Heuristic Function
N-Puzzle supports three different Heuristic Functions:

-   Euclidean Distance
-   Manhattan Distance (City-Block distance)
-   Tiles Out-of-place

I try:
- a* with Manhattan Distance


# Explain Solution implemented
To solve the n-puzzle problem (a simplified sliding puzzle) using the A* search algorithm, the key components are:

1. **State Representation**: Represent the puzzle as a 2D array, where the blank space is denoted by `0`.
2. **Heuristic Function**: Use a heuristic to estimate the cost to the goal. The Manhattan distance is commonly used.
3. **Actions**: Valid moves for the blank space (up, down, left, right).
4. **Priority Queue**: Maintain states in a priority queue sorted by `f(n) = g(n) + h(n)`:
   -  g(n) : Cost to reach the current state.
   -  h(n) : Estimated cost to reach the goal (heuristic).
5. **Goal Test**: Check if the state matches the goal configuration.



## Details

1. **Manhattan Distance**:
   - Calculates the sum of the vertical and horizontal distances for each tile to its goal position.

2. **A* Algorithm**:
   - Uses a priority queue (`heapq`) to select the state with the lowest cost \( f(n) = g(n) + h(n) \).
   - **`open_set` (Priority Queue)**:
      - Stores nodes to explore, ordered by their \( f(n) = g(n) + h(n) \) value.
      - Uses a min-heap for efficient access to the node with the lowest \( f \) score.

   - **`gScore` and `fScore`**:
      - `gScore`: The known cost of the cheapest path from the start node to the current node.
      - `fScore`: The estimated total cost (current distance + heuristic) from the start node to the goal, passing through the current node.

   - **Path Reconstruction**:
      - `cameFrom` keeps track of the previous node for each node, allowing the reconstruction of the path once the goal is reached.

   - **Successors**:
      - Generates successor states using `available_actions` and `do_action`.
      - Evaluates successors using an incremental cost (\( g \)) and a weighted heuristic function (\( h \)).

   - **Conditions for Adding Successors**:
      - A successor node is added to the `open_set` only if the new path is better than any previously found paths.

3. **Actions and Transitions**:
   - `available_actions` generates valid moves for the blank space.
   - `do_action` applies the selected action to produce a new state.

4.  **Print path**
      - `reconstruct_path`: reconstructs the path from the start to the goal by following the cameFrom dictionary, which stores the parent of each node.

# RESULT

| Grid Size | Moves | Time (s) |
|-----------|-------|----------|
| 3x3       | 53    | 0.1      |
| 4x4       | 172   | 9.8      |
| 5x5       | 162   | 6.4      |
| 6x6       | x    | x      |

I couldn't find a way to improve performance for grid sizes larger than 5x5.



## Documentation
https://en.wikipedia.org/wiki/A*_search_algorithm
https://tristanpenman.com/demos/n-puzzle/
https://algorithmsinsight.wordpress.com/graph-theory-2/a-star-in-general/implementing-a-star-to-solve-n-puzzle/