# Sliding Window

Fundamentally this is a two pointer approach

```python
def sliding_window(nums):
    left = 0  # initiate the left boundary of window
    for right in range(len(nums)):  # iterate the right boundary of window
        while is_valid_window:
            left += 1  # Reduce left boundary to shrink window size
```

The template code is fairly simple.

Basically we iterate through the given list, and create a window. 

When there the condition is satisfied (i.e. subset of the list satisfied the required returning condition), we reduce the left side to shrink the window, to find the best solution (most cases its the minimum subset of given list)

Practice:

- [594. Longest Harmonious Subsequence](https://leetcode.com/problems/longest-harmonious-subsequence/)

