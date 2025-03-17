**Example 1:**
**Input:** N = 6, array[] = {13,46,24,52,20,9}
**Output:** 9,13,20,24,46,52
**Explanation:** After sorting we get 9,13,20,24,46,52

**Example 2:**
**Input:** N = 5, array[] = {5,4,3,2,1}
**Output:** 1,2,3,4,5
**Explanation:** After sorting we get 1,2,3,4,5

```
let arr = [13, 46, 24, 52, 20, 9];
var n = arr.length;

function insertion_sort(arr, i, n) {
    if (i == n) return;
    
    let j=i;

    while (j>0 && arr[j-1] > arr[j]) {
        let temp = arr[j-1];
        arr[j-1] = arr[j];
        arr[j] = temp;
        j--;
    }
    insertion_sort(arr, i+1, n);
}

console.log('Before Recursive Insertion Sort :');
console.log(arr);

insertion_sort(arr, 0, n);

console.log('After Recursive Insertion Sort :');
console.log(arr);
```

**Time Complexity:** O(N^2)
**Space Complexity:** O(N)

**Best Case Time Complexity:** O(N)