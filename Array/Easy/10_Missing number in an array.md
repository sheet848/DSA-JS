
### **Summation Approach:**

```

function missingNumber(a, N) {
  // Summation of first N numbers:
  const summation = (N * (N + 1)) / 2;

  // Summation of all array elements:
  let s2 = 0;
  for (let i = 0; i < N - 1; i++) {
    s2 += a[i];
  }

  const missingNum = summation - s2;
  return missingNum;
}

function main() {
  const N = 5;
  const a = [1, 2, 4, 5];
  const ans = missingNumber(a, N);
  console.log("The missing number is:", ans);
}

main();

```

**Time Complexity:** O(N)
**Space Complexity:** O(1) as we are not using any extra space.
