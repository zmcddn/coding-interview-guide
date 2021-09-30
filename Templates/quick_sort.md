# Quick Sort

## Implementation:

- First selects a value (**pivot value**), and then use this value to assist with splitting the list. 
- The actual position where the pivot value belongs in the final sorted list, commonly called the **split point**, will be used to divide the list for subsequent calls to the quick sort. 
- The **partition** process then finds the split point and at the same time move other items to the appropriate side of the list, either less than or greater than the pivot value.
	- Partitioning begins by locating two position markers (i.e. *leftmark* and *rightmark*) at the beginning and end of the remaining items in the list. It will find the split point and at the same time move other items to the appropriate side of the list, either less than or greater than the pivot value.
	- At the point where rightmark becomes less than leftmark, the position of rightmark is now the split point. The pivot value can be exchanged with the contents of the split point and the pivot value is now in place, all the items to the left of the split point are less than the pivot value, and all the items to the right of the split point are greater than the pivot value. The list can now be divided at the split point and the quick sort can be invoked recursively on the two halves.
	- **Median of three:** to choose the median value from the first, the middle, and the last element in the list.
	- time complexity: best case: O(n log n), worst case: O(n2)


## Template

```python
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        """Quick sort solution"""
        
        if not nums:
            return nums
        
        start = 0
        end = len(nums) - 1
        
        self.quick_sort(nums, start, end)
        return nums
    
    def quick_sort(self, nums, start, end):
        if start >= end:
            return nums
        
        left, right = start, end
        pivot = nums[(start+end)//2]
        
        while left <= right:
            while left <= right and nums[left] < pivot:
                left += 1
            
            while left <= right and nums[right] > pivot:
                right -= 1
            
            if left <= right:
                nums[left], nums[right] = nums[right], nums[left]
                left += 1
                right -= 1
                
        self.quick_sort(nums, start, right)
        self.quick_sort(nums, left, end)


class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        """
        Quick sort with 3 partition
        The main idea is that we still have the same pivot point, but 
        instead of comparing with just smaller and greater or equal,
        we take out the equal case and process it individually.
        a[lo,lt-1] < pivot
        a[lt, i-1] = pivot
        a[i,gt] = unseen
        a[gt+1, hi] > pivot
        """
        
        if not nums:
            return nums
        
        start = 0
        end = len(nums) - 1
        
        self.quick_sort(nums, start, end)
        
        return nums
    
    def quick_sort(self, nums, start, end):   
        if start >= end:
            return nums
        
        left = start
        right = end
        index = start
        
        pivot = nums[(start+end)//2]
        
        while index <= right:
            if nums[index] < pivot: 
                nums[index], nums[left] = nums[left], nums[index]
                left += 1
                index += 1
            elif nums[index] > pivot:  
                nums[index], nums[right] = nums[right], nums[index]
                right -= 1
            else:
                index += 1
        
        self.quick_sort(nums, start, left - 1)
        self.quick_sort(nums, right + 1, end)
```


Reference:

- [Quick sort in Python](https://stackabuse.com/quicksort-in-python/)
- [Quicksort 3 way partition](https://gist.github.com/adonese/4bf34d5b57ee0358626c)

Practice:

- [912. Sort an Array](https://leetcode.com/problems/sort-an-array/)
