# Backtracking 

This is essentially the traversal of a decision tree.

There are three things we need to consider:

1. Path (or track)
2. the list of choices
3. End condition

## Template

```python
result = []

def backtrack(track, result, choices):
    if satisfies_end_condition:
        # Here if track is a list we need to do a copy, otherwise we are just appending the pointer to the list's address
        result.append(track.copy())  
        return

    for choice in choices:
        # Make the choice
        track.append(choice)
        backtrack(track, result, choices)
        # undo the choice (i.e. backtrack)
        track.pop()
```


Reference:

- [Leetcode Backtracking Template](https://leetcode.com/explore/learn/card/recursion-ii/472/backtracking/2793/)
- [Backtracking Template](https://github.com/labuladong/fucking-algorithm/blob/english/think_like_computer/DetailsaboutBacktracking.md)

Practice:

- Permutations:
    - [46. Permutations](https://leetcode.com/problems/permutations/)
    - [784. Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/)
    - [47. Permutations II](https://leetcode.com/problems/permutations-ii/)
    - [17. Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
