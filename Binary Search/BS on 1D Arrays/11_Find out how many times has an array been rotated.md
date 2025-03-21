
**Example 1:****Input Format:** arr = [4,5,6,7,0,1,2,3]
**Result:** 4
**Explanation:** The original array should be [0,1,2,3,4,5,6,7]. So, we can notice that the array has been rotated 4 times.

**Example 2:****Input Format:** arr = [3,4,5,1,2]
**Result:** 3
**Explanation:** The original array should be [1,2,3,4,5]. So, we can notice that the array has been rotated 3 times.

# Solution

```Javascript

function findKRotation(arr) {
    let low = 0, high = arr.length - 1;
    let ans = Infinity;
    let index = -1;
    while (low <= high) {
        let mid = Math.floor((low + high) / 2);
        // If search space is already sorted,
        // then arr[low] will always be
        // the minimum in that search space:
        if (arr[low] <= arr[high]) {
            if (arr[low] < ans) {
                index = low;
                ans = arr[low];
            }
            break;
        }

        // If left part is sorted:
        if (arr[low] <= arr[mid]) {
            // Keep the minimum:
            if (arr[low] < ans) {
                index = low;
                ans = arr[low];
            }

            // Eliminate left half:
            low = mid + 1;
        } else { // If right part is sorted:
            // Keep the minimum:
            if (arr[mid] < ans) {
                index = mid;
                ans = arr[mid];
            }

            // Eliminate right half:
            high = mid - 1;
        }
    }
    return index;
}

let arr = [4, 5, 6, 7, 0, 1, 2, 3];
let ans = findKRotation(arr);
console.log("The array is rotated " + ans + " times.");

```

**Time Complexity:** O(logN), N = size of the given array.**Reason:** We are basically using binary search to find the minimum.

**Space Complexity:** O(1)**Reason:** We have not used any extra data structures, this makes space complexity, even in the worst case as O(1).