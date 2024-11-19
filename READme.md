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

try
- a* with Manhattan Distance

To solve the 3-puzzle problem (a simplified sliding puzzle) using the A* search algorithm, the key components are:

1. **State Representation**: Represent the puzzle as a 2D array, where the blank space is denoted by `0`.
2. **Heuristic Function**: Use a heuristic to estimate the cost to the goal. The Manhattan distance is commonly used.
3. **Actions**: Valid moves for the blank space (up, down, left, right).
4. **Priority Queue**: Maintain states in a priority queue sorted by `f(n) = g(n) + h(n)`:
   - \( g(n) \): Cost to reach the current state.
   - \( h(n) \): Estimated cost to reach the goal (heuristic).
5. **Goal Test**: Check if the state matches the goal configuration.



### Explanation of the Code

1. **Manhattan Distance**:
   - Calculates the sum of the vertical and horizontal distances for each tile to its goal position.

2. **A* Algorithm**:
   - Uses a priority queue (`heapq`) to select the state with the lowest cost \( f(n) = g(n) + h(n) \).
   - Keeps track of visited states to avoid revisiting and looping.

3. **Actions and Transitions**:
   - `available_actions` generates valid moves for the blank space.
   - `do_action` applies the selected action to produce a new state.

4. **Path Recording**:
   - Each state stores the sequence of steps leading to it, allowing reconstruction of the solution path.



| **Caratteristica**       | **Greedy Search**                     | **A\* Search**                         |
|--------------------------|---------------------------------------|----------------------------------------|
| **Funzione di valutazione** | \( f(n) = h(n) \)                    | \( f(n) = g(n) + h(n) \)              |
| **Ottimalità**            | Non garantisce la soluzione ottimale  | Garantisce la soluzione ottimale (se l'euristica è ammissibile) |
| **Efficienza**            | Più veloce (meno esplorazione)        | Più lento (più esplorazione)          |
| **Memoria**               | Bassa                                 | Alta (memorizza più nodi)             |
| **Uso dell'euristica**    | Solo euristica \( h(n) \)             | Combinazione di costo del percorso e euristica \( g(n) + h(n) \) |
