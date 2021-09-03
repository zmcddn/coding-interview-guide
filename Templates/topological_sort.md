# Topological Sort

A topological sort takes a directed acyclic graph and produces a linear ordering of all its vertices such that if the graph G contains an edge (v,w) then the vertex v comes before the vertex w in the ordering.

Two important steps for topological sort is:

1. Find the in degree for each node
2. Construct the adjacency list for the graph


```python
def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
    """
    Topological sort, works for DAG (Directed acyclic graph)
    1. Calculate the in-degree for all points, initiate empty adj_list
    2. Put all the 0-degree points (i.e. point that has no neighbor points) into BFS queue
    3. Pop point from BFS queue and put it in the topo queue. Each time of the process visit 
        all the neighbor points and reduce their in-degrees by 1
    4. if the in-degree becomes 0, put them in the queue
    5. End when the queue is empty
    
    https://sugarac.gitbooks.io/facebook-interview-handbook/jiu-zhang-dai-ma-mo-ban.html
    https://leetcode.com/problems/course-schedule-ii/discuss/368716/Python3-Breadth-first-search
    """
    
    # Init a list stores No. of incoming edges of each vertex and 
    # Init map (an adjacency list) to record the node's children
    in_degree = defaultdict(int)
    adj_list = defaultdict(list)
    
    # Build map to put the child into parent's list
    for current_course, prev_course in prerequisites:
        adj_list[prev_course].append(current_course)
        in_degree[current_course] += 1  # a directed edge
    
    #  a queue of all vertices with no incoming edge
    queue = []
    for node in range(numCourses):
        if node not in in_degree:
            queue.append(node)

    res = []
    while queue:
        node = queue.pop(0)  # BFS, pops vertex
        res.append(node)
        for neighbor in adj_list[node]:
            # for each descendant of current vertex, reduce its in-degree by 1
            in_degree[neighbor] -= 1
            
            if in_degree[neighbor] == 0:
                queue.append(neighbor)
                del in_degree[neighbor]
    return res if len(res)==numCourses else []
```

Practice:

- [207. Course Schedule](https://leetcode.com/problems/course-schedule/)
- [210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)
- [1136. Parallel Courses](https://leetcode.com/problems/parallel-courses/)
- [269. Alien Dictionary](https://leetcode.com/problems/alien-dictionary/)
- [1203. Sort Items by Groups Respecting Dependencies](https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies/)


Reference:

- [Topological sort explain (Chinese)](https://sugarac.gitbooks.io/facebook-interview-handbook/content/jiu-zhang-dai-ma-mo-ban.html)
- [Solution for 210](https://leetcode.com/problems/course-schedule-ii/discuss/368716/Python3-Breadth-first-search)
