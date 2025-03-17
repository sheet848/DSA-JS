
```
function linearSearch(arr, num) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === num) {
      return i;
    }
  }
  return -1;
}

// Example usage:
const arr = [1, 2, 3, 4, 5];
const num = 3;
const result = linearSearch(arr, num);
console.log(result); // Output: 2
```

**Time Complexity:** O(n), where n is the length of the array.
**Space Complexity:** O(1)