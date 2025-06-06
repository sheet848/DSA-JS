# **Problem Statement:** 
Given a sorted array of **N integers** and an integer x, write a program to find the upper bound of x.

**Example 1:****Input Format:** N = 4, arr[] = {1,2,2,3}, x = 2
**Result:** 3
**Explanation:** Index 3 is the smallest index such that arr[3] > x.

**Example 2:****Input Format:** N = 6, arr[] = {3,5,8,9,15,19}, x = 9
**Result:** 4
**Explanation:** Index 4 is the smallest index such that arr[4] > x.

### **What is Upper Bound?**

The upper bound algorithm finds the first or the smallest index in a sorted array where the value at that index is greater than the given key i.e. x.

The upper bound is the smallest index, ind, where arr[ind] > x.

## Optimal Solution

```Javascript

function upperBound(arr, x, n) {
    let low = 0, high = n - 1;
    let ans = n;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        // maybe an answer
        if (arr[mid] > x) {
            ans = mid;
            //look for smaller index on the left
            high = mid - 1;
        }
        else {
            low = mid + 1; // look on the right
        }
    }
    return ans;
}

let arr = [3, 5, 8, 9, 15, 19];
let n = 6, x = 9;
let ind = upperBound(arr, x, n);
console.log("The upper bound is the index:", ind);

```

**Time Complexity:** O(logN), where N = size of the given array.  
**Reason:** We are basically using the Binary Search algorithm.

**Space Complexity:** O(1) as we are using no extra space.
