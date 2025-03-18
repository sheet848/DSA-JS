# Problem Statement
**Example 1:****Input:**
 arr = [4, 7, 1, 0]
**Output**:
 7 1 0
**Explanation:**
 Rightmost element is always a leader. 7 and 1 are greater than the elements in their right side.

**Example 2:****Input:**
 arr = [10, 22, 12, 3, 0, 6]
**Output:**
 22 12 6
**Explanation:**
 6 is a leader. In addition to that, 12 is greater than all the elements in its right side (3, 0, 6), also 22 is greater than 12, 3, 0, 6.
## Optimal Approach

```

function printLeaders(arr, n) {

  let ans = [];

  // Last element of an array is always a leader,
  // push into ans array.
  let max = arr[n - 1];
  ans.push(arr[n - 1]);

  // Start checking from the end whether a number is greater
  // than max no. from right, hence leader.
  for (let i = n - 2; i >= 0; i--) {
    if (arr[i] > max) {
      ans.push(arr[i]);
      max = arr[i];
    }
  }

  return ans;
}

// Array Initialization.
let n = 6;
let arr = [10, 22, 12, 3, 0, 6];

let ans = printLeaders(arr, n);

for (let i = ans.length - 1; i >= 0; i--) {
  console.log(ans[i]);
}

```
**Time Complexity: O(N)**
**Space Complexity: O(N)**

