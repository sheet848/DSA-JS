**Problem Statement:** You have been given a non-empty grid **‘mat’** with **'n'** rows and **'m'** columns consisting of only 0s and 1s. All the rows are sorted in ascending order.  
Your task is to find the index of the row with the maximum number of ones.  
**Note:** If two rows have the same number of ones, consider the one with a smaller index. If there's no row with at least 1 zero, return -1.

**Example 1:****Input Format:** n = 3, m = 3, 
mat[] = 
1 1 1
0 0 1
0 0 0
**Result:** 0
**Explanation:** The row with the maximum number of ones is 0 (0 - indexed).

**Example 2:****Input Format:** n = 2, m = 2 , 
mat[] = 
0 0
0 0
**Result:** -1
**Explanation:**  The matrix does not contain any 1. So, -1 is the answer.

# Optimal Solution

```Javascript



function lowerBound(arr, n, x) {
    let low = 0, high = n - 1;
    let ans = n;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        // maybe an answer
        if (arr[mid] >= x) {
            ans = mid;
            // look for smaller index on the left
            high = mid - 1;
        } else {
            low = mid + 1; // look on the right
        }
    }
    return ans;
}

function rowWithMax1s(matrix, n, m) {
    let cnt_max = 0;
    let index = -1;

    // traverse the rows:
    for (let i = 0; i < n; i++) {
        // get the number of 1's:
        let cnt_ones = m - lowerBound(matrix[i], m, 1);
        if (cnt_ones > cnt_max) {
            cnt_max = cnt_ones;
            index = i;
        }
    }
    return index;
}

const matrix = [[1, 1, 1], [0, 0, 1], [0, 0, 0]];
const n = 3, m = 3;
console.log("The row with maximum no. of 1's is: " + rowWithMax1s(matrix, n, m));


```
**Time Complexity:** O(n X logm), where n = given row number, m = given column number.  
**Reason:** We are using a loop running for n times to traverse the rows. Then we are applying binary search on each row with m columns.

**Space Complexity:** O(1) as we are not using any extra space.
