# Network Flow
http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Netflow-All/cover.html

A type of graph problem where the goal is to construct a flow, numerical values on each edge that respect the capacity constraints and that have incoming flow equal to outgoing flow at all vertices except for certain designated terminals.

# (Augmenting Paths)Ford-Fulkerson Algorithm
http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Netflow-All/lecture-1.html

# Minimum Cut

Cut of a graph: Edges that,  were they removed, would seperate the source and sink nodes of a graph

Minimum cut: the smallest amount of these edges that have to be cut

# Greedy DFS

For a Greedy DFS you find the largest path:

Example:

This path would be: A-D-F-G, because it is the largest weight
![](http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Netflow-All/img/Greedy-1.jpg)

# Maximum flow

you can do a form of Dijkstras Algorithim to find the maximum flow of the graph
Example:
This path would be: A-b-c-e-g, because it is the smallest overall weight of 15
![](http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/Netflow-All/img/Greedy-1.jpg)


# Baisically

- The greedy DFS and modified Dijkstra algorithms attempt to minimize the number of paths that you find by finding paths with a lot of flow.
- Greedy DFS is O(|V|log|V|) rather than O(|V|).
- The modified Dijkstra is O(|E|log|V|) rather than O(|E|).