
# Solution

### Example 3: Rotate the array to the right by k positions using the **reversal algorithm**

```
function rotateArrayToRightWithReversal(arr, k) {
  k = k % arr.length;
  reverse(arr, 0, arr.length - k - 1);
  reverse(arr, arr.length - k, arr.length - 1);
  reverse(arr, 0, arr.length - 1);
  return arr;
}

function reverse(arr, start, end) {
  while (start < end) {
    [arr[start], arr[end]] = [arr[end], arr[start]];
    start++;
    end--;
  }
}

const arr = [1, 2, 3, 4, 5, 6, 7];
const k = 2;
console.log(rotateArrayToRightWithReversal(arr, k)); // [6, 7, 1, 2, 3, 4, 5]
```

### Example 4: Rotate the array to the left by k positions using the **reversal algorithm**

```
function rotateArrayToLeftWithReversal(arr, k) {
  k = k % arr.length;
  reverse(arr, 0, k - 1);
  reverse(arr, k, arr.length - 1);
  reverse(arr, 0, arr.length - 1);
  return arr;
}

function reverse(arr, start, end) {
  while (start < end) {
    [arr[start], arr[end]] = [arr[end], arr[start]];
    start++;
    end--;
  }
}

const arr = [1, 2, 3, 4, 5, 6, 7];
const k = 2;
console.log(rotateArrayToLeftWithReversal(arr, k)); // [3, 4, 5, 6, 7, 1, 2]
```

**Time Complexity -** O(N) where N is the number of elements in an array
**Space Complexity -** O(1) since no extra space is required
