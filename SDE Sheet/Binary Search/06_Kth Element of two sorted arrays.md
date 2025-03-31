**Problem Statement:** Given **two sorted arrays** of size **m** and **n** respectively, you are tasked with finding the element that would be at the **kth position** of the **final sorted array**.

# Solution

```Javascript

function kthElement(a, b, m, n, k) {
    if (m > n) return kthElement(b, a, n, m, k);

    let left = k; // length of left half

    // apply binary search:
    let low = Math.max(0, k - n), high = Math.min(k, m);
    while (low <= high) {
        let mid1 = Math.floor((low + high) / 2);
        let mid2 = left - mid1;
        // calculate l1, l2, r1, and r2
        let l1 = Number.MIN_SAFE_INTEGER, l2 = Number.MIN_SAFE_INTEGER;
        let r1 = Number.MAX_SAFE_INTEGER, r2 = Number.MAX_SAFE_INTEGER;
        if (mid1 < m) r1 = a[mid1];
        if (mid2 < n) r2 = b[mid2];
        if (mid1 - 1 >= 0) l1 = a[mid1 - 1];
        if (mid2 - 1 >= 0) l2 = b[mid2 - 1];

        if (l1 <= r2 && l2 <= r1) {
            return Math.max(l1, l2);
        }

        // eliminate the halves:
        else if (l1 > r2) high = mid1 - 1;
        else low = mid1 + 1;
    }
    return 0; // dummy statement
}

let a = [2, 3, 6, 7, 9];
let b = [1, 4, 8, 10];
console.log("The k-th element of two sorted arrays is: " + kthElement(a, b, a.length, b.length, 5));    
        
```

## Complexity Analysis

**Time Complexity:** O(log(min(m, n))), where m and n are the sizes of two given arrays.  
**Reason:** We are applying binary search on the range [max(0, k-n2), min(k, n1)]. The range length <= min(m, n).

**Space Complexity:** O(1), as we are not using any extra space to solve this problem.
