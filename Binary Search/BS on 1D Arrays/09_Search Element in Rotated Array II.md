# **Problem Statement:** 

Given an integer array **arr** of size **N**, sorted in ascending order (**may contain duplicate values**) and a target value **k**. Now the array is rotated at some pivot point unknown to you. Return True if **k** is present and otherwise, return False.

**Example 1:****Input Format:** arr = [7, 8, 1, 2, 3, 3, 3, 4, 5, 6], k = 3
**Result:** True
**Explanation:** The element 3 is present in the array. So, the answer is True.

**Example 2:****Input Format:** arr = [7, 8, 1, 2, 3, 3, 3, 4, 5, 6], k = 10
**Result:** False
**Explanation:** The element 10 is not present in the array. So, the answer is False.

# Optimal Solution

```Javascript

function searchInARotatedSortedArrayII(arr, k) {
    let n = arr.length; // size of the array.
    let low = 0, high = n - 1;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);

        //if mid points the target
        if (arr[mid] === k) return true;

        //Edge case:
        if (arr[low] === arr[mid] && arr[mid] === arr[high]) {
            low = low + 1;
            high = high - 1;
            continue;
        }

        //if left part is sorted:
        if (arr[low] <= arr[mid]) {
            if (arr[low] <= k && k <= arr[mid]) {
                //element exists:
                high = mid - 1;
            }
            else {
                //element does not exist:
                low = mid + 1;
            }
        }
        else { //if right part is sorted:
            if (arr[mid] <= k && k <= arr[high]) {
                //element exists:
                low = mid + 1;
            }
            else {
                //element does not exist:
                high = mid - 1;
            }
        }
    }
    return false;
}

let arr = [7, 8, 1, 2, 3, 3, 3, 4, 5, 6];
let k = 3;
let ans = searchInARotatedSortedArrayII(arr, k);
if (!ans) {
    console.log("Target is not present.");
} else {
    console.log("Target is present in the array.");
}

```

**Time Complexity: O(logN)** for the best and average case. **O(N/2)** for the worst case. Here, N = size of the given array.

**Space Complexity:** O(1)**Reason:** We have not used any extra data structures, this makes space complexity, even in the worst case as O(1).