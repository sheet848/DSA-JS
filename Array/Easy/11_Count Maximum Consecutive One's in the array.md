

```
function findMaxConsecutiveOnes(nums) {
  let cnt = 0;
  let maxi = 0;

  for (let i = 0; i < nums.length; i++) {
    if (nums[i] === 1) {
      cnt++;
    } else {
      cnt = 0;
    }

    maxi = Math.max(maxi, cnt);
  }

  return maxi;
}

const nums = [1, 1, 0, 1, 1, 1];
console.log(findMaxConsecutiveOnes(nums)); // Output: 3

```

**Time Complexity:** O(N)
**Space Complexity:** O(1)
