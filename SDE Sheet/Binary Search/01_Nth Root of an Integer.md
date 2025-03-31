**Problem Statement:** Given two numbers N and M, find the Nth root of M. The nth root of a number M is defined as a number X when raised to the power N equals M. If the 'nth root is not an integer, return -1.

**Example 1:****Input Format:** N = 3, M = 27
**Result:** 3
**Explanation:** The cube root of 27 is equal to 3.

**Example 2:****Input Format:** N = 4, M = 69
**Result:** -1
**Explanation:** The 4th root of 69 does not exist. So, the answer is -1.

# Solution

```Javascript



function func(mid, n, m) {
    let ans = 1;
    for (let i = 1; i <= n; i++) {
        ans = ans * mid;
        if (ans > m) return 2;
    }
    if (ans === m) return 1;
    return 0;
}

function NthRoot(n, m) {
    let low = 1, high = m;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        let midN = func(mid, n, m);
        if (midN === 1) {
            return mid;
        } else if (midN === 0) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return -1;
}

let n = 3, m = 27;
let ans = NthRoot(n, m);
console.log("The answer is: " + ans);



```

## Complexity Analysis

**Time Complexity:** O(logN), N = size of the given array.**Reason:** We are basically using binary search to find the minimum.

**Space Complexity:** O(1)**Reason:** We have not used any extra data structures, this makes space complexity, even in the worst case as O(1).
