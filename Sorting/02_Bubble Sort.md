**Example 1:**
**Input:** N = 6, array[] = {13,46,24,52,20,9}
**Output:** 9,13,20,24,46,52
**Explanation:** After sorting we get 9,13,20,24,46,52

**Input:** N = 5, array[] = {5,4,3,2,1}
**Output:** 1,2,3,4,5
**Explanation:** After sorting we get 1,2,3,4,5

-> checking if swap is done or not, if completed early we can exit early

```
let arr = [13, 46, 24, 52, 20, 9];
var n = arr.length;

function bubble_sort(arr, n) {
    for(let i=n-1; i>=0; i--) {
	    let didSwap = 0;
        for(let j=0; j<=i-1; j++) {
            if(arr[j] > arr[j+1]) {
                let temp = arr[j+1];
                arr[j+1] = arr[j];
                arr[j] = temp;
                didSwap = 1;
            }
        }
    }

    console.log(arr);
}

console.log('Before using bubble sort:');
console.log(arr);

console.log('After bubble sort:');
bubble_sort(arr,n);
```

**Time Complexity :** O(n2)
**Space Complexity** : O(1)