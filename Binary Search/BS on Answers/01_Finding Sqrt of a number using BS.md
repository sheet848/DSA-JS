**Problem Statement:** You are given a positive integer n. Your task is to find and return its square root. If ‘n’ is not a perfect square, then return the floor value of 'sqrt(n)'.

**Example 1:****Input Format:** n = 36
**Result:** 6
**Explanation:** 6 is the square root of 36.

**Example 2:****Input Format:** n = 28
**Result:** 5
**Explanation:** Square root of 28 is approximately 5.292. So, the floor value will be 5.

# Solution

```Javascript



function floorSqrt(n) {
    let low = 1, high = n;
    // Binary search on the answers:
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        let val = mid * mid;
        if (val <= n) {
            // Eliminate the left half:
            low = mid + 1;
        }
        else {
            // Eliminate the right half:
            high = mid - 1;
        }
    }
    return high;
}

let n = 28;
let ans = floorSqrt(n);
console.log("The floor of square root of " + n + " is: " + ans);


```

## Complexity Analysis

**Time Complexity:** O(logN), N = size of the given array.  
**Reason:** We are basically using the Binary Search algorithm.

**Space Complexity:** O(1) as we are not using any extra space.