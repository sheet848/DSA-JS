Here's an optimal solution to print a matrix in a spiral order using JavaScript:

```javascript
function spiralOrder(matrix) {
    const result = [];
    let top = 0, bottom = matrix.length - 1;
    let left = 0, right = matrix[0].length - 1;

    while (top <= bottom && left <= right) {
        // Traverse from left to right along the top row
        for (let i = left; i <= right; i++) {
            result.push(matrix[top][i]);
        }
        top++;

        // Traverse from top to bottom along the right column
        for (let i = top; i <= bottom; i++) {
            result.push(matrix[i][right]);
        }
        right--;

        if (top <= bottom) {
            // Traverse from right to left along the bottom row
            for (let i = right; i >= left; i--) {
                result.push(matrix[bottom][i]);
            }
            bottom--;
        }

        if (left <= right) {
            // Traverse from bottom to top along the left column
            for (let i = bottom; i >= top; i--) {
                result.push(matrix[i][left]);
            }
            left++;
        }
    }

    return result;
}

// Example Usage:
const matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

console.log(spiralOrder(matrix));
// Output: [1, 2, 3, 6, 9, 8, 7, 4, 5]
```

### Explanation:
1. **Define Boundaries**: Maintain four boundaries—`top`, `bottom`, `left`, and `right`—to track the part of the matrix being processed.
2. **Traversal**:
   - Start with the top row, moving left to right.
   - Continue down the right column, then the bottom row (right to left), and finally the left column (bottom to top).
   - Adjust the boundaries (`top`, `bottom`, `left`, `right`) after completing each traversal.
3. **Repeat Until Done**: Repeat the above steps until all elements are added to the result array.

This solution works efficiently in **O(m × n)** time complexity, where `m` and `n` are the matrix's dimensions. It doesn't modify the input matrix and uses minimal additional space.

Let me know if you'd like me to explain any part of the code further!