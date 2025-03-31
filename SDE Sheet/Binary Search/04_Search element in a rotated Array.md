# ****Problem Statement:**** 

Given an integer array arr of size N, sorted in ascending order (with distinct values) and a target value k. Now the array is rotated at some pivot point unknown to you. Find the index at which k is present and if k is not present return -1.

Example 1:
Input Format: arr = [4,5,6,7,0,1,2,3], k = 0
Result: 4
Explanation: Here, the target is 0. We can see that 0 is present in the given rotated sorted array, nums. Thus, we get output as 4, which is the index at which 0 is present in the array.

Example 2:
Input Format: arr = [4,5,6,7,0,1,2], k = 3
Result: -1
Explanation: Here, the target is 3. Since 3 is not present in the given rotated sorted array. Thus, we get the output as -1.

# Optimal Solution

```Javascript

function search(arr, n, k) {
    let low = 0, high = n - 1;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);

        // if mid points to the target
        if (arr[mid] === k) return mid;

        // if left part is sorted
        if (arr[low] <= arr[mid]) {
            if (arr[low] <= k && k <= arr[mid]) {
                // element exists
                high = mid - 1;
            } else {
                // element does not exist
                low = mid + 1;
            }
        } else { // if right part is sorted
            if (arr[mid] <= k && k <= arr[high]) {
                // element exists
                low = mid + 1;
            } else {
                // element does not exist
                high = mid - 1;
            }
        }
    }
    return -1;
}

let arr = [7, 8, 9, 1, 2, 3, 4, 5, 6];
let n = 9, k = 1;
let ans = search(arr, n, k);
if (ans === -1)
    console.log("Target is not present.");
else
    console.log("The index is:", ans);



```


**Time Complexity:** O(logN), N = size of the given array.**Reason:** We are using binary search to search the target.

**Space Complexity:** O(1)**Reason:** We have not used any extra data structures, this makes space complexity, even in the worst case as O(1).
