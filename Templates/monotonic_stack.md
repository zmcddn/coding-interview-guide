# Monotonic Stack 

- A monotonic stack is a special form stack inside which all elements are sorted in either ascending or descending order

## Template

```python
def monotonic_stack(nums):
    """An increasing monotonic stack, all elements are sorted in ascending order"""

    stack = []
    res = [-1] * len(nums)

    # Template for descending traversal
    for i in range(len(nums)-1, -1, -1):
        while stack and nums[stack[-1]] <= nums[i]:
            stack.pop()   # Remove existing element that is smaller than incoming element
        if stack:
            res[i] = nums[stack[-1]]
        stack.append(i)  # use for next iteration

    # # Template for ascending traversal
    # for i in range(len(nums)):
    #     while stack and (nums[stack[-1]] < nums[i]):
    #         res[stack.pop()] = nums[i]
    #     stack.append(i)
    return res
```

Reference:

- [Using monotonic stack w/ analysis](https://leetcode.com/problems/next-greater-element-i/discuss/1113246/Cpp-Using-monotonic-stack-w-analysis)

Practice:

- [496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)
- [503. Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)
- [739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)
- [1019. Next Greater Node In Linked List](https://leetcode.com/problems/next-greater-node-in-linked-list/)
- [316. Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/)
- [402. Remove K Digits](https://leetcode.com/problems/remove-k-digits/)
- [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
- [84. Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)
