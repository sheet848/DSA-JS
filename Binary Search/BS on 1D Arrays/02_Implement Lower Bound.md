# **Problem Statement:** 

Given a sorted array of **N integers** and an integer x, write a program to find the lower bound of x.

**Example 1:****Input Format:** N = 4, arr[] = {1,2,2,3}, x = 2
**Result:** 1
**Explanation:** Index 1 is the smallest index such that arr[1] >= x.

**Example 2:****Input Format:** N = 5, arr[] = {3,5,8,15,19}, x = 9
**Result:** 3
**Explanation:** Index 3 is the smallest index such that arr[3] >= x.

### **What is Lower Bound?**

The lower bound algorithm finds the first or the smallest index in a sorted array where the value at that index is greater than or equal to a given key i.e. x.

The lower bound is the smallest index, ind, where arr[ind] >= x. But **_if any such index is not found_**, the lower bound algorithm returns n i.e. size of the given array.

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
        }
        else {
            low = mid + 1; // look on the right
        }
    }
    return ans;
}

let arr = [3, 5, 8, 15, 19];
let n = 5, x = 9;
let ind = lowerBound(arr, n, x);
console.log("The lower bound is the index:", ind);


```

**Time Complexity:** O(logN), where N = size of the given array.  
**Reason:** We are basically using the Binary Search algorithm.

**Space Complexity:** O(1) as we are using no extra space.