# Strongly Connected Components

- This is probably won't be in an interview, so code implementation is not provided, but good to know the concepts
- **Strongly Connected Component (SCC):** a strongly connected component C, of a graph G, as the largest subset of vertices C⊂V such that for every pair of vertices v,w∈C we have a path from v to w and a path from w to v.    
![](http://interactivepython.org/runestone/static/pythonds/_images/scc1.png)
- Once the strongly connected components have been identified we can show a simplified view of the graph by combining all the vertices in one strongly connected component into a single larger vertex.    
![](http://interactivepython.org/runestone/static/pythonds/_images/scc2.png)
- The transposition of a graph G is defined as the graph G^T where all the edges in the graph have been reversed.

## Implementation

1. Call DFS for the graph G to compute the finish times for each vertex.
2. Compute G^T (i.e. transposition of G)
3. Call DFS for the graph G^T but in the main loop of DFS explore each vertex in decreasing order of finish time
4. Each tree in the forest computed in step 3 is a strongly connected component. Output the vertex ids for each vertex in each tree in the forest to identify the component

## Reference:

- [Strongly Connected Components](https://runestone.academy/runestone/books/published/pythonds/Graphs/StronglyConnectedComponents.html)
