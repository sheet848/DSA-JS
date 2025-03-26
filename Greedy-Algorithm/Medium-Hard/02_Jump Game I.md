**Problem Statement:** Given an array where each element represents the maximum number of steps you can jump forward from that element, return true if we can reach the last index starting from the first index. Otherwise, return false.

**Example 1:****Input:**nums = [2, 3, 1, 0, 4]
**Output:** True
**Explanation:** 
1. We start at index 0, with value 2 this means we can jump to index 1 or 2.
2. From index 1, with value 3, we can jump to index 2, 3, or 4. However, if we jump to index 2 with value 1, we can only jump to index 3.
3. So we jump to index 1 then index 4 reaching the end of the array.

Hence, we return true.

**Example 2:****Input:**nums = [3, 2, 1, 0, 4]
**Output:** False
**Explanation:** 
1. We start at index 0, with value 3 which means we can jump to index 1, 2, or 3.
2. From index 1, with value 2 we can only jump to index 2 or 3.
3. From index 2, with value 1 we can only jump to index 3.
4. From index 3, with value 0 we cannot jump any further.

Hence, from all possibilities we are unable to jump to the last index so we return false.

# Solution

```Javascript
                            
function canJump(nums) {
    // Initialize the maximum
    // index that can be reached
    let maxIndex = 0;

    // Iterate through each
    // index of the array
    for (let i = 0; i < nums.length; i++) {
        // If the current index is greater
        // than the maximum reachable index
        // it means we cannot move forward
        // and should return false
        if (i > maxIndex) {
            return false;
        }

        // Update the maximum index
        // that can be reached by comparing
        // the current maxIndex with the sum of
        // the current index and the
        // maximum jump from that index
        maxIndex = Math.max(maxIndex, i + nums[i]);
    }

    // If we complete the loop,
    // it means we can reach the
    // last index
    return true;
}

function main() {
    let nums = [4, 3, 7, 1, 2];

    console.log("Array representing maximum jump from each index: ");
    for (let i = 0; i < nums.length; i++) {
        console.log(nums[i] + " ");
    }
    console.log();

    let ans = canJump(nums);

    if (ans) {
        console.log("It is possible to reach the last index.");
    } else {
        console.log("It is not possible to reach the last index.");
    }
}

main();

```

**Time Complexity: O(N)** where N is the length of the input array. We iterate through the input array exactly once and at each element perform constant time operations.

**Space Complexity: O(1)** as the algorithm uses only a constant amount of extra space regardless of the size of the input array. It does not require any additional data structures that scale with the input size.