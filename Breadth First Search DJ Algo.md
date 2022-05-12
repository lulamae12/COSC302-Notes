# Breadth First Search
lecture notes link: https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/BFS/


Breadth First Search (BFS) is complementary to Depth First Search (DFS). DFS works by visiting a node and then recursively visiting children. You can view it as relying on a stack -- push a node onto a stack, then go through the following algorithm:
1. Pop a node off the stack.
2. Do some processing on the node.
3. Push all of the node's children onto the stack in reverse order.
4. Repeat until the stack is empty.


The node's "back-link". This is the node that pushed it.

BFS is the same as a DFS but it works with a qeeue

Running time is O(|V|+|E|)

# Dijkstra's Algortihim

Dijkstra's Algroithim is a modified version of a BFS, where it finds the shortest path from node to node based off edge weights.

```
set everynode to a backlink of null, a distance of -1 and the visited feild to false

set the starting nodes distance to 0

now repeat the following:
    -remove a node n from the map and set its visited var to true
    
    -For each edge e from n to n2 such that n2 has not been visited. Let d be n's distance plus the weight of edge e. If n2's distance is -1, or if d is less than node n2's current distance:



    Set n2's distance to d.
    Set n2's back-link to e.
    Insert n2 into the multimap, keyed on distance.

```

when this is done the backlinks should represent the shortest path


## Example:

What is the shortest path of this graph from 0 to 6?

![](http://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/BFS/img/Ex-Graph-W.png)
