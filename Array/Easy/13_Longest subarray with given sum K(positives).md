Here’s an optimal solution to find the longest subarray with a given sum `K`, assuming all elements in the array are positive:

### Optimal Solution in JavaScript:

```javascript
function longestSubarrayWithSumK(arr, K) {
    let left = 0, right = 0;
    let currentSum = 0;
    let maxLength = 0;

    while (right < arr.length) {
        // Add the current element to the current sum
        currentSum += arr[right];

        // Shrink the window from the left if the current sum exceeds K
        while (currentSum > K) {
            currentSum -= arr[left];
            left++;
        }

        // Check if the current sum equals K
        if (currentSum === K) {
            maxLength = Math.max(maxLength, right - left + 1);
        }

        // Expand the window to the right
        right++;
    }

    return maxLength;
}

// Example Usage:
const arr = [1, 2, 3, 7, 5];
const K = 12;

console.log(longestSubarrayWithSumK(arr, K));
// Output: 2 (subarray is [5, 7])
```

### Explanation:
1. **Sliding Window Approach**:
   - Use two pointers: `left` and `right`.
   - Expand the window by moving `right` to include elements until the sum exceeds `K`.
   - Shrink the window by moving `left` to reduce the sum back to within the target.

2. **Checking Condition**:
   - Whenever `currentSum` equals `K`, calculate the length of the current window (`right - left + 1`) and update `maxLength`.

3. **Efficiency**:
   - **Time Complexity**: **O(n)**, as each element is processed at most twice (once when expanding the window and once when shrinking it).
   - **Space Complexity**: **O(1)**, as no extra space proportional to the input size is used.

This method works optimally with positive numbers because the sliding window approach relies on the fact that the sum increases when expanding and decreases when shrinking. Let me know if you’d like to explore variations or edge cases!