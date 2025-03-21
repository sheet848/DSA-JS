**Problem Statement:** You are given a sorted array containing N integers and a number X, you have to find the occurrences of X in the given array.

**Example 1:****Input:** N = 7,  X = 3 , array[] = {2, 2 , 3 , 3 , 3 , 3 , 4}
**Output**: 4
**Explanation:** 3 is occurring 4 times in 
the given array so it is our answer.

**Example 2:****Input:** N = 8,  X = 2 , array[] = {1, 1, 2, 2, 2, 2, 2, 3}
**Output**: 5
**Explanation:** 2 is occurring 5 times in the given array so it is our answer.

# Optimal Solution

```Javascript

function firstOccurrence(arr, n, k) {
    let low = 0, high = n - 1;
    let first = -1;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        // maybe an answer
        if (arr[mid] === k) {
            first = mid;
            // look for smaller index on the left
            high = mid - 1;
        }
        else if (arr[mid] < k) {
            low = mid + 1; // look on the right
        }
        else {
            high = mid - 1; // look on the left
        }
    }
    return first;
}

function lastOccurrence(arr, n, k) {
    let low = 0, high = n - 1;
    let last = -1;

    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        // maybe an answer
        if (arr[mid] === k) {
            last = mid;
            // look for larger index on the right
            low = mid + 1;
        }
        else if (arr[mid] < k) {
            low = mid + 1; // look on the right
        }
        else {
            high = mid - 1; // look on the left
        }
    }
    return last;
}

function firstAndLastPosition(arr, n, k) {
    let first = firstOccurrence(arr, n, k);
    if (first === -1) return [-1, -1];
    let last = lastOccurrence(arr, n, k);
    return [first, last];
}

function count(arr, n, x) {
    let [first, last] = firstAndLastPosition(arr, n, x);
    if (first === -1) return 0;
    return last - first + 1;
}

let arr = [2, 4, 6, 8, 8, 8, 11, 13];
let n = 8, x = 8;
let ans = count(arr, n, x);
console.log("The number of occurrences is:", ans);


```
**Time Complexity:** O(2*logN), where N = size of the given array.  
**Reason:** We are basically using the binary search algorithm twice.

**Space Complexity:** O(1) as we are using no extra space.

