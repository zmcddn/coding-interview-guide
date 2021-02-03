# Binary Search

***The KEY is the search interval***

## Generic template

Find a number in a list of distinct sorted numbers, return -1 if there is no such number.

Time complexity: `O(logn)`

```python
def generic_binary_search(nums, target):
    left = 0
    right = len(nums) - 1

    while left <= right:
        mid = left + (right - left) // 2
        if nums[mid] < target:
            left = mid + 1
        elif nums[mid] > target:
            right = mid - 1
        elif nums[mid] == target:
            return mid

    return -1
```

Search interval: `[left, right]`

Practice: [704. Binary Search](https://leetcode.com/problems/binary-search/submissions/)

## Search left

Find the first target in a list of sorted numbers with duplication, return -1 if there is no such number.

```python
def binary_search_left(nums, target):
    if not nums:
        return -1

    left = 0
    right = len(nums)

    while left < right:
        mid = left + (right - left) // 2
        if nums[mid] < target:
            left = mid + 1
        elif nums[mid] > target:
            right = mid
        elif nums[mid] == target:
            right = mid

    return left if nums[left] == target else -1
```

Search interval: `[left, right)`

## Search right

Find the last target in a list of sorted numbers with duplication, return -1 if there is no such number.

```python
def binary_search_left(nums, target):
    if not nums:
        return -1

    left = 0
    right = len(nums)

    while left < right:
        mid = left + (right - left) // 2
        if nums[mid] < target:
            left = mid + 1
        elif nums[mid] > target:
            right = mid
        elif nums[mid] == target:
            left = mid + 1

    return left - 1 if nums[left - 1] == target else -1
```

Search interval: `[left, right)`

# Universal template

```python
def generic_binary_search(nums, target):
    left = 0
    right = len(nums) - 1

    while left <= right:
        mid = left + (right - left) // 2
        if nums[mid] < target:
            left = mid + 1
        elif nums[mid] > target:
            right = mid - 1
        elif nums[mid] == target:
            return mid

            # # search left
            # right = mid - 1

            # # search right
            # left = mid + 1

    return -1

    # # search left
    # return -1 if left >= len(nums) or nums[left] != target else left

    # # search right
    # return -1 if right < 0 or nums[right] != target else right
```

Search interval: `[left, right]`

# Python builtin function

You can also use the builtin `biset` function to do the same thing.

[Details here](https://docs.python.org/3/library/bisect.html)


Practice:

- [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
