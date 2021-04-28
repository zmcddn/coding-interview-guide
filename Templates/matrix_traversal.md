# Matrix Traversal

Here we are using 2D matrix as example, but the idea could be applied to multi-dimension matrix

## Template

## Generic Template

```python
def traverse(matrix):
    rows, cols = len(matrix), len(matrix[0])

    for row in range(rows):
        for col in range(cols):
            print(matrix[row][col])
```

## Transpose Matrix

```python
def transpose(matrix):
    rows, cols = len(matrix), len(matrix[0])

    for row in range(rows):
        for col in range(row, cols):
            matrix[row][col], matrix[col][row] = matrix[col][row], matrix[row][col]
```

## Reverse Row

```python
def reverse_row(matrix):
    rows, cols = len(matrix), len(matrix[0])

    for row in range(rows):
        for col in range(cols//2):
            matrix[row][col], matrix[row][cols-1-col] = matrix[row][cols-1-col], matrix[row][col]
```

## Reverse Column

```python
def reverse_col(matrix):
    rows, cols = len(matrix), len(matrix[0])

    for row in range(rows//2):
        for col in range(cols):
            matrix[row][col], matrix[rows-1-row][col] = matrix[rows-1-row][col], matrix[row][col]
```

## Rotation Template

- Rotate 90 degrees clockwise: transpose + reverse row
- Rotate 90 degrees anti-clockwise: transpose + reverse column
- Rotate 180 degrees: reverse row + reverse column

## Spiral Traverse

This one is a bit tricky, and the idea is a little different than above.

Instead of looping through each column and then row, we can iterate through the total number of coordinates and increment row and col count accordingly.

This idea can also be used in above rotations.

```python
def spiral_matrix(matrix):
    rows, cols = len(matrix), len(matrix[0])

    row, col, k = 0, 0, 0  # k is the boarder level
    for _ in range(rows * cols):
        # Note the order here is important
        if row == k:  # Top
            if col == cols - 1 - k:  # Top right
                row += 1
            else:
                col += 1
            continue

        if col == cols - 1 - k:  # Right
            if row == rows - 1 - k:  # Bottom Right
                col -= 1
            else:
                row += 1
            continue

        if row == rows - 1 - k:  # Bottom
            if col == k:  # Bottom Left
                row -= 1
            else:
                col -= 1
            continue

        if col == k:  # Left
            row -= 1
            if row == k:  # Boarder complete, go 1 layer inside
                k += 1
                row += 1
                col += 1
```


Reference:

- [Rotate 90 clockwise, anti-clockwise, and rotate 180 degree](https://leetcode.com/problems/rotate-image/discuss/401356/Rotate-90-clockwise-anti-clockwise-and-rotate-180-degree)

Practice:

- [766. Toeplitz Matrix](https://leetcode.com/problems/toeplitz-matrix/)
- [74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)
- [867. Transpose Matrix](https://leetcode.com/problems/transpose-matrix/)
- [832. Flipping an Image](https://leetcode.com/problems/flipping-an-image/)
- [48. Rotate Image](https://leetcode.com/problems/rotate-image/)
- [54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)
