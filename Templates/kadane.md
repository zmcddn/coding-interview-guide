# Kadane's Algorithm 

- Kadane's Algorithm is an algorithm that can find the **maximum sum subarray** given an array of numbers in *O(n)* time and *O(1)* space

## Implementation

- Iterating through the array using an integer variable `current`, and at each index `i`, determines if elements before index `i` are "worth" keeping, or if they should be "discarded". 

1. best = negative infinity
2. current = 0
3. for num in nums:
    3.1. current = Max(current + num, num)
    3.2. best = Max(best, current)

4. return best

## Template

```python
def maxSubArray(self, nums: List[int]) -> int:
    # Initialize our variables using the first element.
    current = best = nums[0]
     
    for num in nums[1:]:
        # If current is negative, throw it away. Otherwise, keep adding to it.
        current = max(num, current + num)
        best = max(best, current)
     
    return best
```


Reference:

- [Leetcode Kadane's Algorithm](https://leetcode.com/explore/learn/card/dynamic-programming/633/common-patterns-continued/4140/)
- [Kadane’s Algorithm Explained \| HackerNoon](https://hackernoon.com/kadanes-algorithm-explained-50316f4fd8a6)

Practice:

- [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
- [152. Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
- [918. Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)
- [1014. Best Sightseeing Pair](https://leetcode.com/problems/best-sightseeing-pair/)
