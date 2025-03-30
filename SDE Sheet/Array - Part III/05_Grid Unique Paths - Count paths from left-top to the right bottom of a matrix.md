**Problem Statement:** Given a matrix **m X n**, count paths from left-top to the right bottom of a matrix with the constraints that from each cell you can either only move to the rightward direction or the downward direction.

**Input Format**: m = 2, n= 2
**Output:** 2

**Input Format**: m = 2, n= 3 
**Ouput:** 3

# Solution

Here's an optimal solution to calculate the number of unique paths in a grid using JavaScript, leveraging dynamic programming:

```javascript
function uniquePaths(m, n) {
    // Create a 2D array for DP
    const dp = Array.from({ length: m }, () => Array(n).fill(1));
    
    // Fill the DP table based on recurrence relation
    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
        }
    }
    
    return dp[m - 1][n - 1]; // Return bottom-right corner
}

// Example usage
console.log(uniquePaths(3, 7)); // Output: 28
console.log(uniquePaths(2, 3)); // Output: 3
```

### Explanation:

1. **Base Case**:
    
    - The first row and first column of the grid can only have one path because you can only move right or down.
2. **Dynamic Programming Transition**:
    
    - For each cell `(i, j)`, the number of unique paths to reach it is the sum of paths from the cell above `(i-1, j)` and the cell to the left `(i, j-1)`: [ dp[i][j] = dp[i-1][j] + dp[i][j-1] ]
3. **Efficiency**:
    
    - Time complexity: (O(m \times n)) since we compute paths for all cells.
    - Space complexity: (O(m \times n)) for the DP array.

This approach efficiently computes the number of paths while avoiding repeated calculations, making it a great choice for larger grids!