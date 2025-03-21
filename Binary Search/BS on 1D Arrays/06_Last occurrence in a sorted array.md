To find the **last occurrence** of a target value in a sorted array using Binary Search, you can achieve an **O(log n)** time complexity. Below is the optimal solution:

---

### Implementation
```javascript
function findLastOccurrence(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    let result = -1; // Default if the target is not found

    while (left <= right) {
        const mid = Math.floor((left + right) / 2);

        if (nums[mid] === target) {
            result = mid; // Update result to current index
            left = mid + 1; // Move to the right half to search for the last occurrence
        } else if (nums[mid] < target) {
            left = mid + 1; // Move to the right half
        } else {
            right = mid - 1; // Move to the left half
        }
    }

    return result;
}

// Example Usage
const nums = [1, 2, 2, 2, 3, 4, 5];
const target = 2;

console.log(findLastOccurrence(nums, target)); // Output: 3
console.log(findLastOccurrence(nums, 3)); // Output: 4
console.log(findLastOccurrence(nums, 6)); // Output: -1 (Not found)
```

---

### Explanation
1. **Initialization:**
   - Use two pointers, `left` and `right`, to define the search range.
   - Use a `result` variable to store the index of the last occurrence when found.

2. **Binary Search Logic:**
   - Calculate the middle index: `mid = Math.floor((left + right) / 2)`.
   - If `nums[mid] === target`:
     - Store `mid` in `result`.
     - Move to the right half (`left = mid + 1`) to keep searching for the last occurrence.
   - If `nums[mid] < target`:
     - Move to the right half (`left = mid + 1`).
   - If `nums[mid] > target`:
     - Move to the left half (`right = mid - 1`).

3. **Return Value:**
   - If the target is not found, `result` will remain `-1`.

---

### Example Walkthrough
For `nums = [1, 2, 2, 2, 3, 4, 5]` and `target = 2`:
- Initial `left = 0`, `right = 6`.
- 1st iteration: `mid = 3`, `nums[3] = 2`. Update `result = 3` and move `left = 4`.
- 2nd iteration: `mid = 5`, `nums[5] > 2`. Move `right = 4`.
- Search ends, last occurrence is at index `3`.

---

This approach is efficient and avoids unnecessary iterations. Let me know if you'd like me to explain further or adapt this to specific scenarios!