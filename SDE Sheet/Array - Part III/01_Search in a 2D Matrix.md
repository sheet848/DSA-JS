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

**Time Complexity:** O(log(NxM)), where N = given row number, M = given column number.  
**Reason:** We are applying binary search on the imaginary 1D array of size NxM.

**Space Complexity:** O(1) as we are not using any extra space.