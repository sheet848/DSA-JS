**Example 1:**
**Input:** N=5, arr[]={4,2,1,6,7}
**Output:** 1,2,4,6,7,

**Example 2:**
**Input:** N=7,arr[]={3,2,8,5,1,4,23}
**Output:** 1,2,3,4,5,8,23

- Merge Sort is a **divide and conquers algorithm**, it divides the given array into equal parts and then merges the 2 sorted parts.
- There are 2 main functions :
	- **merge():** This function is used to merge the 2 halves of the array. It assumes that both parts of the array are sorted and merges both of them.
	- **mergeSort():** This function divides the array into 2 parts. low to mid and mid+1 to high where,
```
low = leftmost index of the array
high = rightmost index of the array
mid = Middle index of the array
```
- We recursively split the array, and go from top-down until all sub-arrays size becomes 1.

```
let arr = [13, 46, 24, 52, 20, 9];

function merge(left, right) {
    const result = [];
    let i = 0;
    let j = 0;

    while (i< left.length && j < right.length) {
        if(left[i] <= right[j]) {
            result.push(left[i]);
            i++;
        } else {
            result.push(right[j]);
            j++;
        }
    }
    
    return result.concat(left.slice(i)).concat(right.slice(j));

}

function mergeSort(arr) {
    if(arr.length <= 1) {
        return arr;
    }

    const mid = Math.floor(arr.length / 2);
    const left = arr.slice(0, mid);
    const right = arr.slice(mid);
    
    return merge(mergeSort(left), mergeSort(right));
}

console.log('Before using merge sort:');
console.log(arr);
const sortedArr = mergeSort(arr);
console.log('After merge sort:');
console.log(sortedArr);
```
**Time Complexity :** O(nlogn)
**Space Complexity :** O(n)

**Auxiliary Space Complexity :** O(n)
