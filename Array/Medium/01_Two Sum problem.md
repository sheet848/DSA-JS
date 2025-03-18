# Problem Statement

**Example 1:**
**Input Format:** N = 5, arr[] = {2,6,5,8,11}, target = 14
**Result:** YES (for 1st variant)
       [1, 3] (for 2nd variant)
**Explanation:** arr[1] + arr[3] = 14. So, the answer is “YES” for the first variant and [1, 3] for 2nd variant.

**Example 2:**
**Input Format:** N = 5, arr[] = {2,6,5,8,11}, target = 15
**Result:** NO (for 1st variant)
	[-1, -1] (for 2nd variant)
**Explanation:** There exist no such two numbers whose sum is equal to the target.
### Optimized Approach ( Two Pointer )

```
function twoSum(n, arr, target) {
    arr.sort((a, b) => a - b);
    let left = 0, right = n - 1;
    while (left < right) {
        let sum = arr[left] + arr[right];
        if (sum === target) {
            return "YES";
        } else if (sum < target) {
            left++;
        } else {
            right--;
        }
    }
    return "NO";
}

let n = 5;
let arr = [2, 6, 5, 8, 11];
let target = 14;
let ans = twoSum(n, arr, target);
console.log(`This is the answer for variant 1: ${ans}`);
```

**Time Complexity:** O(N) + O(N*logN)
**Space Complexity:** O(1)
