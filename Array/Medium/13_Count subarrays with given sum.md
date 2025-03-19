Here's the equivalent JavaScript implementation of the provided C++ code. The logic remains the same, adapted for JavaScript syntax and conventions:

```javascript
function findAllSubarraysWithGivenSum(arr, k) {
    const prefixSumMap = new Map(); // Map to store prefix sums
    let preSum = 0; // Tracks the current prefix sum
    let count = 0; // Count of subarrays

    // Base case: Initialize prefix sum 0 with a count of 1
    prefixSumMap.set(0, 1);

    for (let i = 0; i < arr.length; i++) {
        // Add current element to prefix sum
        preSum += arr[i];

        // Calculate the value to remove
        const remove = preSum - k;

        // Check if the required prefix sum exists in the map
        if (prefixSumMap.has(remove)) {
            count += prefixSumMap.get(remove);
        }

        // Update the map with the current prefix sum
        prefixSumMap.set(preSum, (prefixSumMap.get(preSum) || 0) + 1);
    }

    return count;
}

// Example usage:
const arr = [3, 1, 2, 4];
const k = 6;

const result = findAllSubarraysWithGivenSum(arr, k);
console.log(`The number of subarrays is: ${result}`);
// Output: The number of subarrays is: 2
```

### Explanation:
1. **Prefix Sum Map**: A `Map` is used to store the frequency of prefix sums encountered so far.
2. **Base Case**: Prefix sum `0` is initialized with a count of `1` to account for subarrays starting from the beginning of the array.
3. **Logic**:
   - At each iteration, compute the prefix sum.
   - Check if `preSum - k` exists in the map, which indicates a subarray with the given sum `k`.
   - Update the count of subarrays and the frequency of the current prefix sum.
4. **Efficiency**:
   - Time Complexity: **O(n)**, where `n` is the length of the array.
   - Space Complexity: **O(n)**, for the `Map` storing prefix sums.

Let me know if you'd like any additional explanation!
