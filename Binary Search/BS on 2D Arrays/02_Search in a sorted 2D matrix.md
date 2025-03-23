**Problem Statement:** You have been given a 2-D array **'mat'** of size **'N x M'** where **'N'** and **'M'** denote the number of rows and columns, respectively. The elements of each row are sorted in non-decreasing order. Moreover, the first element of a row is greater than the last element of the previous row (if it exists). You are given an integer **‘target’**, and your task is to find if it exists in the given 'mat' or not.

**Example 1:
Input Format:** N = 3, M = 4, target = 8,
mat[] = 
1 2 3 4
5 6 7 8 
9 10 11 12
**Result:** true
**Explanation:** The ‘target’  = 8 exists in the 'mat' at index (1, 3).

**Example 2:
Input Format:** N = 3, M = 3, target = 78,
mat[] = 
1 2 4
6 7 8 
9 10 34
**Result:** false
**Explanation:** The ‘target' = 78 does not exist in the 'mat'. Therefore in the output, we see 'false'.

# Optimal Solution

```Javascript



function searchMatrix(matrix, target) {
    let n = matrix.length;
    let m = matrix[0].length;

    // apply binary search:
    let low = 0, high = n * m - 1;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        let row = Math.floor(mid / m);
        let col = mid % m;
        
        if (matrix[row][col] === target) return true;
        else if (matrix[row][col] < target) low = mid + 1;
        else high = mid - 1;
    }
    return false;
}

let matrix = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]];
let result = searchMatrix(matrix, 8);
console.log(result ? "true" : "false");


```

## Complexity Analysis

**Time Complexity:** O(log(NxM)), where N = given row number, M = given column number.  
**Reason:** We are applying binary search on the imaginary 1D array of size NxM.

**Space Complexity:** O(1) as we are not using any extra space.
