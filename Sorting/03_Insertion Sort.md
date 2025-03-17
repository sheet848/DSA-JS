**Example 1:**
**Input:** N = 6, array[] = {13,46,24,52,20,9}
**Output:** 9,13,20,24,46,52
**Explanation:** 
After sorting the array is: 9,13,20,24,46,52

**Example 2:**
**Input:** N=5, array[] = {5,4,3,2,1}
**Output:** 1,2,3,4,5
**Explanation:** After sorting the array is: 1,2,3,4,5

```
let arr = [13, 46, 24, 52, 20, 9];
var n = arr.length;

function insertion_sort(arr, n) {
    for (let i=0; i<=n-1; i++) {
        let j=i;
        while (j>0 && arr[j-1] > arr[j]) {
            let temp = arr[j-1];
            arr[j-1] = arr[j];
            arr[j] = temp;
            j--;
        }
    }

    console.log(arr);
}

console.log('Before using bubble sort:');
console.log(arr);

console.log('After bubble sort:');
insertion_sort(arr,n);
```

**Time Complexity :** O(n2)
**Space Complexity** : O(1)

best time complexity will come when the array is already sorted then it becomes O(N)