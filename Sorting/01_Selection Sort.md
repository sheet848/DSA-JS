Example 1:**
**Input:** N = 6, array[] = {13,46,24,52,20,9}
**Output:** 9,13,20,24,46,52
**Explanation:** After sorting the array is: 9, 13, 20, 24, 46, 52

**Example 2:**
**Input:** N=5, array[] = {5,4,3,2,1}
**Output:** 1,2,3,4,5
**Explanation:** After sorting the array is: 1, 2, 3, 4, 5

```
let arr = [13, 46, 24, 52, 20, 9];
var n = arr.length;

function selection_sort(arr, n) {
    for(let i=0; i<n-1; i++) {
    
   // find min element in array
        let min = i;
        for(let j=i+1; j<n; j++) {
            if (arr[j] < arr[min]) {
                min=j;
            }
        }
	// swapping position with the smallest
        let temp = arr[min];
        arr[min] = arr[i];
        arr[i] = temp;
    }
    // printing sorted array
    console.log(arr);
}

console.log('Before selection sort:');
console.log(arr);

console.log('After selection sort:');
selection_sort(arr, n);

```

**Time Complexity** : O(N^2)
**Space Complexity** : O(1)
