**Problem Statement:** You have been given a 2-D array **'mat'** of size **'N x M'** where **'N'** and **'M'** denote the number of rows and columns, respectively. The elements of each row and each column are sorted in non-decreasing order.  
But, the first element of a row is not necessarily greater than the last element of the previous row (if it exists).  
You are given an integer **‘target’**, and your task is to find if it exists in the given 'mat' or not.

**Input Format:** N = 5, M = 5, target = 14
mat[] = 
![](http://takeuforward.org/wp-content/uploads/2023/08/Ex1.png)**Result:** true
**Explanation:** Target 14 is present in the cell (3, 2)(0-based indexing) of the matrix. So, the answer is true.

**Example 2:
Input Format:** N = 3, M = 3, target = 12,
mat[] = 
![](http://takeuforward.org/wp-content/uploads/2023/08/Ex2.png)**Result:** false
**Explanation:** As target 12 is not present in the matrix, the answer is false.

# Optimal Solution

```Javascript



function searchElement(matrix, target) {
    let n = matrix.length;
    let m = matrix[0].length;
    let row = 0;
    let col = m - 1;

    // Traverse the matrix from (0, m-1):
    while (row < n && col >= 0) {
        if (matrix[row][col] === target) return true;
        else if (matrix[row][col] < target) row++;
        else col--;
    }
    return false;
}

const matrix = [
    [1, 4, 7, 11, 15],
    [2, 5, 8, 12, 19],
    [3, 6, 9, 16, 22],
    [10, 13, 14, 17, 24],
    [18, 21, 23, 26, 30]
];

const result = searchElement(matrix, 8);
console.log(result ? "true" : "false");


```

**Output:** true

## Complexity Analysis

**Time Complexity:** O(N+M), where N = given row number, M = given column number.  
**Reason:** We are starting traversal from (0, M-1), and at most, we can end up being in the cell (M-1, 0). So, the total distance can be at most (N+M). So, the time complexity is O(N+M).

**Space Complexity:** O(1) as we are not using any extra space.