# Merge Sort

## Implementation:

- A recursive algorithm that continually splits a list in half. 
- If the list is empty or has one item, it is sorted by definition (the base case). 
- Once the two halves are sorted, the **merge** operation, which takes two smaller sorted lists and combining them together into a single, sorted, new list. 
- time complexity: O(n log n)


## Template

```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        """Merge sort solution"""
        
        if not nums:
            return nums
        
        start = 0
        end = len(nums) - 1
        
        return self.merge_sort(nums, start, end, temp=[-1 for i in nums])
    
    def merge_sort(self, nums, start, end, temp):
        if start >= end:
            return nums
        
        mid = (start + end) // 2
        
        self.merge_sort(nums, start, mid, temp)
        self.merge_sort(nums, mid+1, end, temp)
        return self.merge(nums, start, mid, end, temp)
    
    def merge(self, nums, start, mid, end, temp):
        left = start
        right = mid + 1
        index = start
        
        while left <= mid and right <= end:
            if nums[left] <= nums[right]:
                temp[index] = nums[left]
                left += 1
            else:
                temp[index] = nums[right]
                right += 1
            
            index += 1
        
        while left <= mid:
            temp[index] = nums[left]
            index += 1
            left += 1
        
        while right <= end:
            temp[index] = nums[right]
            index += 1
            right += 1
            
        for i in range(start, end+1):
            nums[i] = temp[i]
            index += 1
        
        return nums
```


Reference:

- [Merge sort in Python - stackabuse](https://stackabuse.com/merge-sort-in-python/)
- [Merge sort in Python - educative](https://www.educative.io/edpresso/merge-sort-in-python)

Practice:

- [912. Sort an Array](https://leetcode.com/problems/sort-an-array/)
