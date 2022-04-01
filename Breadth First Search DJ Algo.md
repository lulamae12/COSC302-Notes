# Breadth First Search
lecture notes link: https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/BFS/

---

Breadth First Search (BFS) is complementary to Depth First Search (DFS). DFS works by visiting a node and then recursively visiting children. You can view it as relying on a stack -- push a node onto a stack, then go through the following algorithm:
1. Pop a node off the stack.
2. Do some processing on the node.
3. Push all of the node's children onto the stack in reverse order.
4. Repeat until the stack is empty.

Now, breadth-first search works in the same manner, only we use a queue instead of a stack, and we push the children onto the queue in their proper order. Additionally, instead of a "visited" field, we are going to keep two pieces of data with each node:

The node's distance from node zero. Whenever a node is pushed onto the queue, you set its distance to be the distance of the node that pushed it, plus one.
The node's "back-link". This is the node that pushed it.

BFS is the same but it works with a qeue

Running time is O(|V|+|E|)