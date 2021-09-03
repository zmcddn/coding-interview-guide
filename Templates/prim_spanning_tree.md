# Prim’s Spanning Tree Algorithm

- This is probably won't be in an interview, so code implementation is not provided, but good to know the concepts
- The algorithm is for solving the problem to efficiently transfer a piece of information to anyone and everyone who may be listening.
- **uncontrolled flooding:** the broadcast host sends a single copy of the broadcast message and lets the routers sort things out (i.e. the brute force way)
    - Each message starts with a time to live (*ttl*) value set to some number greater than or equal to the number of edges between the broadcast host and its most distant listener
    - Each router gets a copy of the message and passes the message on to all of its neighboring routers. 
    - When the message is passed on the *ttl* is decreased. Each router continues to send copies of the message to all its neighbors until the *ttl* value reaches 0.
- **Minimum weight spanning tree:** define a minimum spanning tree T for a graph G=(V,E) such that T is an acyclic subset of E that connects all the vertices in V. The sum of the weights of the edges in T is minimized.
    - the broadcast host sends a single copy of the broadcast message into the network
    - Each router forwards the message to any neighbor that is part of the spanning tree, excluding the neighbor that just sent it the message

## Prim’s algorithm

- Prim’s algorithm belongs to the “greedy algorithms” family because at each step it chooses the cheapest next step, which is to follow the edge with the lowest weight in the spanning tree case
- Algorithm:
    - while T is not yet a spanning tree
        - Find an edge that is safe to add to the tree
        - Add the new edge to T
- A **safe edge** is any edge that connects a vertex that is in the spanning tree to a vertex that is not in the spanning tree
- The algorithm is similar to Dijkstra’s algorithm and also uses a priority queue to select the next vertex to add to the growing graph
    - Select a starting node, and initialize all the other vertices to infinity
    - A node is not considered to be part of the spanning tree until it is removed from the priority queue.
    - Always examine the smallest distance and update the predecessor links

## Reference:

- [Prim’s Spanning Tree Algorithm](https://runestone.academy/runestone/books/published/pythonds/Graphs/PrimsSpanningTreeAlgorithm.html)
