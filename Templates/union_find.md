# Union Find 

- Union Find (or disjoint-set) is a very elegant data structure
- Essentially it utilizes a list representation for the joint data points
    - the index of the data point indicates its linkage status
- For detailed explanation, please see this [Lecture Notes](https://www.cs.princeton.edu/~rs/AlgsDS07/01UnionFind.pdf)

## Template

```python
class UnionFind:
    def __init__(self, n):
        self.count = n
        self.parent = list(range(n))  # root list
        self.size = [1] * n  # weight
        
    def find(self, i):
        while self.parent[i] != i:
            self.parent[i] = self.parent[self.parent[i]]  # Path compression
            i = self.parent[i]
        return i
    
    def union(self, p, q):
        i, j = self.find(p), self.find(q)
        
        if i == j:
            return 

        # merge smaller tree into larger tree to obtain a flat structure
        if self.size[i] < self.size[j]:
            self.parent[i] = j
            self.size[j] += self.size[i]
        else:
            self.parent[j] = i
            self.size[i] += self.size[j]
        
        self.count -= 1
```


Reference:

- [Union Find with Explanations (Java / Python)](https://leetcode.com/problems/redundant-connection/discuss/123819/Beats-97.96-Union-Find-Java-with-Explanations)
- [[Python] Solved by Union Find Template](https://leetcode.com/problems/couples-holding-hands/discuss/391618/python-solved-by-union-find-template)
- [Python, Weighted Union+Find with Path Compression](https://leetcode.com/problems/number-of-provinces/discuss/1244070/Python-Weighted-Union%2BFind-with-Path-Compression)
- [[Python3] Classic Union Find Solution](https://leetcode.com/problems/number-of-islands-ii/discuss/1083904/Python3-Classic-Union-Find-Solution)

Practice:

- [684. Redundant Connection](https://leetcode.com/problems/redundant-connection/)
- [547. Number of Provinces](https://leetcode.com/problems/number-of-provinces/)
- [765. Couples Holding Hands](https://leetcode.com/problems/couples-holding-hands/)
- [305. Number of Islands II](https://leetcode.com/problems/number-of-islands-ii/)
