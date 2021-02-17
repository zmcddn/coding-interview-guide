# Dijkstra’s algorithm (Shortest Path)

## Implementation:

- Use an instance variable keep track of the total cost from the start node to each destination
- The instance variable will contain the current total weight of the smallest weight path from the start to the vertex in question
- The algorithm iterates once for every vertex in the graph (order is in priority queue)
- The PriorityQueue class stores tuples of key, value pairs
    - the key in the priority queue must match the key of the vertex in the graph
    - the value is used for deciding the priority, and thus the position of the key in the priority queue


***Essentially, this is a BFS using priority queue instead of queue***


Reference:

- [Dijkstra’s Algorithm](https://runestone.academy/runestone/books/published/pythonds/Graphs/DijkstrasAlgorithm.html)

Practice:

- [Please Share dijkstra's algorithm questions - Leetcode](https://leetcode.com/discuss/interview-question/731911/please-share-dijkstras-algorithm-questions)

