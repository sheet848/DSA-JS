**Example 1:**
**Input:** N = 6, array[] = {13,46,24,52,20,9}
**Output:** 9,13,20,24,46,52
**Explanation:** After sorting we get 9,13,20,24,46,52

**Example 2:**
**Input:** N = 5, array[] = {5,4,3,2,1}
**Output:** 1,2,3,4,5
**Explanation:** After sorting we get 1,2,3,4,5

- Now, in the recursive approach, we will just select the range recursively instead of using any loop. This is the only change we will do the recursive bubble sort algorithm and the rest of the part will be completely the same as it was in the case of iterative bubble sort.

```
bubble_sort(6);
bubble_sort(5);
bubble_sort(4);
bubble_sort(3);
bubble_sort(2);
bubble_sort(1);
```

**The Approach**

```
let arr = [13, 46, 24, 52, 20, 9];
var n = arr.length;

function bubble_sort(arr, n) {
  if (n==1) return;
  
  for(let j=0; j<=n-2; j++) {
    if(arr[j] > arr[j+1]) {
      let temp = arr[j+1];
      arr[j+1] = arr[j];
      arr[j] = temp;
    }
  }
  bubble_sort(arr, n-1);
}

console.log('Before Recursive Bubble Sort :');
console.log(arr);

bubble_sort(arr, n);

console.log('After Recursive Sort :');
console.log(arr);
```

**Time Complexity:** O(N^2)
**Space Complexity:** O(N)

**Optimized Approach**

```
let arr = [13, 46, 24, 52, 20, 9];
var n = arr.length;

function bubble_sort(arr, n) {
  if (n==1) return;
  let didSwap = 0;

  for(let j=0; j<=n-2; j++) {
    if(arr[j] > arr[j+1]) {
      let temp = arr[j+1];
      arr[j+1] = arr[j];
      arr[j] = temp;
      didSwap = 1;
    }
  }
  if(didSwap == 0) return;

  bubble_sort(arr, n-1);
}

console.log('Before Recursive Bubble Sort :');
console.log(arr);

bubble_sort(arr, n);

console.log('After Recursive Sort :');
console.log(arr);
```

**Time Complexity:** O(N2) for the worst and average cases and O(N) for the best case.
**Space Complexity:** O(N)