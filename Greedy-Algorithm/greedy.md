# Greedy Algorithm

A **greedy algorithm** is a problem-solving method that builds up a solution piece by piece, always choosing the most optimal choice available at each step without considering the overall problem. The "greedy" part refers to making the choice that seems best at the moment, hoping it will lead to the global optimum.

### Key Features:
1. **Local Optimization**: Makes decisions based on the current state, selecting the best immediate option.
2. **No Reconsideration**: Once a choice is made, it isn't revisited or changed.
3. **Efficient**: Usually has a simpler implementation and faster runtime than other approaches like dynamic programming.

### When to Use:
Greedy algorithms work well when:
- The problem has an **optimal substructure** (optimal solutions to sub-problems can be combined to solve the main problem).
- The problem exhibits a **greedy-choice property**, meaning a locally optimal choice leads to a globally optimal solution.

### Examples of Greedy Algorithms:
- **Huffman Coding** (for data compression)
- **Dijkstra's Algorithm** (shortest path in a weighted graph)
- **Kruskal's and Prim's Algorithms** (for finding minimum spanning trees)
- **Activity Selection Problem** (scheduling activities to maximize the number of non-overlapping events)
- **Coin Change Problem** (if coins are in standard denominations).

Although greedy algorithms are fast and efficient, they are not always guaranteed to provide the correct or optimal solution for every problem, especially when the problem does not have a greedy-choice property. In such cases, other techniques like dynamic programming might be better suited. Let me know if you’d like an example of a specific problem solved using a greedy algorithm!
