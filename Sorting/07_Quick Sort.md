**Example 1:**
**Input:**  N = 5  , Arr[] = {4,1,7,9,3}
**Output:** 1 3 4 7 9 

**Explanation:** After sorting the array becomes 1, 3, 4, 7, 9

**Example 2:**
**Input:** N = 8 , Arr[] = {4,6,2,5,7,9,1,3}
**Output:** 1 2 3 4 5 6 7 9
**Explanation:** After sorting the array becomes 1, 3, 4, 7, 9

**Intuition:**
- Quick Sort is a divide-and-conquer algorithm like [the Merge Sort](https://takeuforward.org/data-structure/merge-sort-algorithm/). But unlike Merge sort, this algorithm does not use any extra array for sorting(though it uses an auxiliary stack space). So, from that perspective, Quick sort is slightly better than Merge sort.
- This algorithm is basically a repetition of two simple steps that are the following:
	- Pick a pivot and place it in its correct place in the sorted array.
	- Shift smaller elements(i.e. Smaller than the pivot) on the left of the pivot and larger ones to the right.

**Optimized APPROACH**

-> three divisions of array

```
function quickSort(arr) {
    if (arr.length <= 1) {
        return arr;
    }

    let pivot = arr[Math.floor(arr.length / 2)];
    let left = [];
    let middle = [];
    let right = [];

    for (let i = 0; i < arr.length; i++) {
        if (arr[i] < pivot) {
            left.push(arr[i]);
        } else if (arr[i] === pivot) {
            middle.push(arr[i]);
        } else {
            right.push(arr[i]);
        }
    }

    return quickSort(left).concat(middle, quickSort(right));

}

let arr = [64, 34, 25, 12, 22, 11, 90];
console.log("Original array:", arr);
arr = quickSort(arr);
console.log("Sorted array:", arr);
```

**Time Complexity:** O(N*logN)
**Space Complexity:** O(1) + O(N)
