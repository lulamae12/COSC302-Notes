# Graphs And DFS
lecture notes link: https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/DFS/

https://en.wikipedia.org/wiki/Glossary_of_graph_theory

look up:vertices, edges, adjacency, incidence, directed/undirected, path, cycle, loop, multiedge, connected component, bipartite.
---
directed graphs have arrows or the like 
undiriected do not


graphs have nodes

edges are the "lines of the arrows and such"


## Incidince and Adjaceny

do yhis later

## cylce
a cycle is a path from a node to itself that doesnt contain a node twice

## bipartite

bipartite graph: nodes are partitoned into two sets and each node has a edge that goes to a node in the othe graph

## note
egdes and nodes can have propertys known as weights

---
# Graph representation

There are infinite ways to represent graphs. There are three main ways that you should know:
- Using adjacency lists.
- Using an adjacency matrix.
- Mathematically.


# Adjaceny lists

for each node you have a list of the nodes to which this node has edges

![](https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/DFS/img/g1.jpg)

![](https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/DFS/img/AdjList.jpg)

# Adjaceny matrix

a matrix if you look in col i row j

if i has a edge to j the value of i,j will be 1

if not it will be 0



# Mathematical Representation

When computer scientists write about graphs, they often use a more mathematical representation. They typically define a graph as: `
```
G = { V, E }

V = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 }
E = { (1,3), (3,5), (4,6), (4,7), (4,9), (6,8) }
```
- V is a set of vertices
- E is a set of edges

## example

![](https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/DFS/img/PQ.jpg)
```
G = { V, E }

V = { i | 0 ≤ i < n }
E = { (u,v) | u,v ∈ V and v = 2u+1 or v = 2u+2 }

For all u ∈ V, there is a numeric value val(u).
If (u,v) ∈ E, then val(u) ≤ val(v).
```

---
# Depth First Search

one of the most basic graph algorithms

 With DFS, each node has a boolean value called visited. Before the DFS, that value is set to false, for all nodes. Then, you commence a DFS on a node. Let's call that node n. The DFS works as follows:
- Check n's visited field. If true, then return.
- Set n's visited field to true.
- Optionally do some activity on n.
- Then, for all edges of the form (n,u) call DFS on u.
- Optionally Do some final activity on n.
- Return.

When you call DFS on a node n, the DFS will visit every node connected to n. For that reason, DFS is good for activities that involve connectivity.

DFS  Basically is a search algor where you keep track of the nodes that have been visited and that have not


