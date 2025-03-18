# Problem Statement

**Example 1:****Input:** arr = [-2,1,-3,4,-1,2,1,-5,4] 

**Output:** 6 

**Explanation:** [4,-1,2,1] has the largest sum = 6. 

**Examples 2:****Input:** arr = [1] 

**Output:** 1 

**Explanation:** Array has only one element and which is giving positive sum of 1.
## Optimal Approach

```

function maxSubarraySum(arr, n) {
    let maxi = Number.MIN_SAFE_INTEGER; // maximum sum
    let sum = 0;

    for (let i = 0; i < n; i++) {
        sum += arr[i];

        if (sum > maxi) {
            maxi = sum;
        }

        // If sum < 0: discard the sum calculated
        if (sum < 0) {
            sum = 0;
        }
    }

    // To consider the sum of the empty subarray
    // uncomment the following check:

    //if (maxi < 0) maxi = 0;

    return maxi;
}

const arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4];
const n = arr.length;
const maxSum = maxSubarraySum(arr, n);
console.log("The maximum subarray sum is: " + maxSum);

```

**Time Complexity:** O(N)
**Space Complexity:** O(1)

---
# Follow Up Question
There might be more than one subarray with the maximum sum. We need to print any of them.

```

function maxSubarraySum(arr, n) {
    let maxi = Number.MIN_SAFE_INTEGER; // maximum sum
    let sum = 0;

    let start = 0;
    let ansStart = -1, ansEnd = -1;
    for (let i = 0; i < n; i++) {

        if (sum == 0) start = i; // starting index

        sum += arr[i];

        if (sum > maxi) {
            maxi = sum;

            ansStart = start;
            ansEnd = i;
        }

        // If sum < 0: discard the sum calculated
        if (sum < 0) {
            sum = 0;
        }
    }

    //printing the subarray:
    console.log("The subarray is: [");
    for (let i = ansStart; i <= ansEnd; i++) {
        console.log(arr[i] + " ");
    }
    console.log("]n");

    // To consider the sum of the empty subarray
    // uncomment the following check:

    //if (maxi < 0) maxi = 0;

    return maxi;
}

let arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4];
let n = arr.length;
let maxSum = maxSubarraySum(arr, n);
console.log("The maximum subarray sum is: " + maxSum);

```

**Time Complexity:** O(N)
**Space Complexity:** O(1)
