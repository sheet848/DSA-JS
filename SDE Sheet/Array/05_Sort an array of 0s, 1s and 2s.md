**Problem Statement:** Given an array consisting of only 0s, 1s, and 2s. Write a program to in-place sort the array without using inbuilt sort functions. ( Expected: Single pass-O(N) and constant space)

**Input:** nums = [2,0,2,1,1,0]
**Output**: [0,0,1,1,2,2]

**Input:** nums = [2,0,1]
**Output:** [0,1,2]

**Input:** nums = [0]
**Output:** [0]

# Optimal Approach

Dutch National Flag

```Javascript
function sortArray(arr) {
    let low = 0, mid = 0, high = arr.length - 1; // 3 pointers

    while (mid <= high) {
        if (arr[mid] === 0) {
            [arr[low], arr[mid]] = [arr[mid], arr[low]]; // swap 0s
            low++;
            mid++;
        } else if (arr[mid] === 1) {
            mid++;
        } else {
            [arr[mid], arr[high]] = [arr[high], arr[mid]]; // swap 2s
            high--;
        }
    }
}

// Example usage:
const arr = [0, 2, 1, 2, 0, 1];
sortArray(arr);
console.log("After sorting:");
console.log(arr.join(" ")); // Output: 0 0 1 1 2 2

```

**Time Complexity:** O(N) **Space Complexity:** O(1)