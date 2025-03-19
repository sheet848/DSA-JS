To find the **longest subarray with a given sum K**, including arrays with both positive and negative numbers, we can use a **prefix sum** combined with a **hash map** for efficient processing.

Here’s the JavaScript implementation:

```javascript
function longestSubarrayWithSumK(arr, K) {
    const prefixSumMap = new Map();
    let prefixSum = 0;
    let maxLength = 0;

    for (let i = 0; i < arr.length; i++) {
        // Add the current element to the prefix sum
        prefixSum += arr[i];

        // Check if the prefix sum is exactly K
        if (prefixSum === K) {
            maxLength = i + 1; // Subarray starts from index 0 to i
        }

        // Check if (prefixSum - K) exists in the map
        if (prefixSumMap.has(prefixSum - K)) {
            // Update the maximum length
            maxLength = Math.max(maxLength, i - prefixSumMap.get(prefixSum - K));
        }

        // Store the first occurrence of the prefix sum
        if (!prefixSumMap.has(prefixSum)) {
            prefixSumMap.set(prefixSum, i);
        }
    }

    return maxLength;
}

// Example Usage:
const arr = [1, 2, 3, -2, 5];
const K = 6;

console.log(longestSubarrayWithSumK(arr, K));
// Output: 3 (subarray is [1, 2, 3])
```

### Explanation:
1. **Prefix Sum**:
   - The sum of elements from the beginning of the array to the current position.
   - If `prefixSum - K` exists in the map, it means there’s a subarray with sum `K` between the stored index and the current index.

2. **Hash Map**:
   - Tracks the first occurrence of each prefix sum.
   - Allows for O(1) lookup to check if `(prefixSum - K)` exists.

3. **Logic**:
   - If the `prefixSum` equals `K`, update the `maxLength` to include the entire subarray from the beginning.
   - Otherwise, calculate the length of the subarray using the stored index of `(prefixSum - K)`.

4. **Efficiency**:
   - **Time Complexity**: **O(n)**, as we traverse the array once and perform constant-time operations for each element.
   - **Space Complexity**: **O(n)**, for storing prefix sums in the hash map.

This approach works efficiently with both positive and negative numbers. Let me know if you'd like additional examples or a deeper breakdown!