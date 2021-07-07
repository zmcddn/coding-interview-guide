# Sliding Window

***Fundamentally this is a two pointer approach***

How it works:

- A general way is to use a hashmap assisted with two pointers.
- Use two pointers: start and end to represent a window.
- Move end to find a valid window.
- When a valid window is found, move start to find a smaller window.
- To check if a window is valid, we use a map to store (char, count) for chars in t, and use counter for the number of chars of t to be found in s.

There are two keys here:
1. the two pointers both start from the beginning of the second string initially
2. move j until `j - i == len(first_string)`


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


Reference:

- [Leetcode 567 detailed explanation](https://leetcode.com/problems/permutation-in-string/discuss/638531/Java-or-C%2B%2B-or-Python3-or-Detailed-explanation-or-O(N)-time)
- [10-line template that can solve most 'substring' problems
](https://leetcode.com/problems/minimum-window-substring/discuss/26808/here-is-a-10-line-template-that-can-solve-most-substring-problems)
- [Sliding Window algorithm template to solve all the Leetcode substring search problem.](https://leetcode.com/problems/find-all-anagrams-in-a-string/discuss/92007/Sliding-Window-algorithm-template-to-solve-all-the-Leetcode-substring-search-problem.)


Practice:

- [594. Longest Harmonious Subsequence](https://leetcode.com/problems/longest-harmonious-subsequence/)
- [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- [159. Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)
- [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
- [1156. Swap For Longest Repeated Character Substring](https://leetcode.com/problems/swap-for-longest-repeated-character-substring/)
- [1004. Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)
- [76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
- [30. Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)
