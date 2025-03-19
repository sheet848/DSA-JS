Here’s an optimal solution for rotating a matrix by 90 degrees clockwise using JavaScript. This approach efficiently rotates the matrix in-place if required:

```javascript
function rotateMatrix(matrix) {
    const n = matrix.length;

    // Step 1: Transpose the matrix
    for (let i = 0; i < n; i++) {
        for (let j = i; j < n; j++) {
            [matrix[i][j], matrix[j][i]] = [matrix[j][i], matrix[i][j]];
        }
    }

    // Step 2: Reverse each row
    for (let i = 0; i < n; i++) {
        matrix[i].reverse();
    }

    return matrix;
}

// Example Usage:
const matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

console.log(rotateMatrix(matrix));
// Output:
// [
//   [7, 4, 1],
//   [8, 5, 2],
//   [9, 6, 3]
// ]
```

### Explanation:
1. **Transpose the Matrix**: Swap matrix\[i\]\[j\] with matrix\[j\]\[i\]. This converts rows into columns and columns into rows.
2. **Reverse Each Row**: Reverse every row in the transposed matrix to complete the 90-degree rotation.

This algorithm operates with **O(n²)** time complexity and modifies the matrix in-place, optimizing space usage.

Let me know if you'd like me to walk through any part of the code!