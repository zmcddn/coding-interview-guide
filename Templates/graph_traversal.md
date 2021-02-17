# Graph Traversal - BFS/DFS

We can use either BFS or DFS to traversal the graph

## Recursive template

```python
def traverse(matrix):
    """Recursive"""
    
    rows, cols = len(matrix), len(matrix[0])
    visited = set()
    directions = ((0, 1), (0, -1), (1, 0), (-1, 0))  # Much faster than list

    def dfs(i, j):
        if (i, j) in visited:
            return
        visited.add((i, j))
        
        # Traverse neighbors
        for direction in directions:
            next_i, next_j = i + direction[0], j + direction[1]
            if 0 <= next_i < rows and 0 <= next_j < cols: # Check boundary
                # Add any other checking here ^
                dfs(next_i, next_j)
            
    for i in range(rows):
        for j in range(cols):
            dfs(i, j)
```

## Iterative template

```python
# BFS TEmplate for LC 200

def numIslands(self, grid: List[List[str]]) -> int:
    count = 0

    if not grid:
        return count

    rows = len(grid)
    cols = len(grid[0])
    directions = ((0, 1), (0, -1), (1, 0), (-1, 0))

    for row in range(rows):
        for col in range(cols):
            if grid[row][col] == '1':
                # The position here is critical
                # count here means counting all the "1"s
                count += 1
                grid[row][col] = 'visited' # Mark current node as visited
                queue = [(row, col)]  # Initiate a queue for bfs

                while queue:
                    for _ in range(len(queue)):
                        # Must use name other than row and col
                        # Otherwise there will be collision
                        x, y = queue.pop(0)

                        for _x,_y in directions:
                            # Trasversal all directions
                            dx, dy = x + _x, y + _y

                            if dx > rows-1 or dx < 0 or dy > cols-1 or dy < 0 or grid[dx][dy] != "1":
                                continue

                            grid[dx][dy] = 'visited'
                            queue.append((dx, dy))
                            
                            # if count is here (i.e. inside all loops) it'll count how many "1"s
                    
                    # If count is here, (i.e. out of the two for loops) 
                    # it'll count how many steps it'll need from the position 
                    # to go to all the other places (i.e. leetcode 994)

    return count
```

Reference:

- [Tips for all DFS in matrix question](https://leetcode.com/problems/pacific-atlantic-water-flow/discuss/90739/python-dfs-bests-85-tips-for-all-dfs-in-matrix-question)

Practice:

- [200. Number of Islands](https://leetcode.com/problems/number-of-islands/)
- [130. Surrounded Regions](https://leetcode.com/problems/surrounded-regions/)
- [695. Max Area of Island](https://leetcode.com/problems/max-area-of-island/)
- [994. Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)

