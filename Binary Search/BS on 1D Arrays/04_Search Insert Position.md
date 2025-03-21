# **Problem Statement:** 
You are given a sorted array **arr** of distinct values and a target value **x**. You need to search for the index of the target value in the array.

If the value is present in the array, then return its index. Otherwise, determine the index where it would be inserted in the array while maintaining the sorted order.

**Example 1:**
**Input Format:** arr[] = {1,2,4,7}, x = 6
**Result:** 3
**Explanation:** 6 is not present in the array. So, if we will insert 6 in the 3rd index(0-based indexing), the array will still be sorted. {1,2,4,6,7}.

**Example 2:**
**Input Format:** arr[] = {1,2,4,7}, x = 2
**Result:** 1
**Explanation:** 2 is present in the array and so we will return its index i.e. 1.

---
## Solution

Here’s the optimal solution to find the **Search Insert Position** using Binary Search in JavaScript. This approach ensures an efficient time complexity of **O(log n)**.

### Problem
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

---

### Implementation
```javascript
function searchInsertPosition(nums, target) {
    let left = 0;
    let right = nums.length - 1;

    while (left <= right) {
        const mid = Math.floor((left + right) / 2);

        if (nums[mid] === target) {
            return mid; // Target found
        } else if (nums[mid] < target) {
            left = mid + 1; // Move to the right half
        } else {
            right = mid - 1; // Move to the left half
        }
    }

    // If not found, left will point to the insert position
    return left;
}

// Example Usage
const nums = [1, 3, 5, 6];
const target = 5;

console.log(searchInsertPosition(nums, target)); // Output: 2
console.log(searchInsertPosition(nums, 2)); // Output: 1 (Insert position)
console.log(searchInsertPosition(nums, 7)); // Output: 4 (Insert position)
console.log(searchInsertPosition(nums, 0)); // Output: 0 (Insert position)
```

---

### Explanation
1. **Initialization:**
   - Use two pointers, `left` and `right`, to define the search range.

2. **Binary Search Logic:**
   - Calculate the middle index: `mid = Math.floor((left + right) / 2)`.
   - If the target is equal to `nums[mid]`, return `mid`.
   - If the target is greater than `nums[mid]`, move the `left` pointer to `mid + 1`.
   - If the target is smaller than `nums[mid]`, move the `right` pointer to `mid - 1`.

3. **Insert Position:**
   - If the target is not found, the `left` pointer will indicate the position where the target should be inserted to maintain order.

---

This approach makes use of Binary Search for optimal efficiency. If you’d like, I can walk you through modifications or discuss edge cases like empty arrays! Let me know.