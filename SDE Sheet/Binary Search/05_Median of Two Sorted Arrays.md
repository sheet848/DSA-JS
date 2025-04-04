**Problem Statement:** Given **two sorted arrays** arr1 and arr2 of size m and n respectively, return the **median** of the two sorted arrays. The median is defined as the middle value of a sorted list of numbers. In case the length of the list is even, the median is the average of the two middle elements.

**Example 1:**
**Input Format:** n1 = 3, arr1[] = {2,4,6}, n2 = 3, arr2[] = {1,3,5}
**Result:** 3.5
**Explanation:** The array after merging 'a' and 'b' will be { 1, 2, 3, 4, 5, 6 }. As the length of the merged list is even, the median is the average of the two middle elements. Here two medians are 3 and 4. So the median will be the average of 3 and 4, which is 3.5.

**Example 2:**
**Input Format:** n1 = 3, arr1[] = {2,4,6}, n2 = 2, arr2[] = {1,3}
**Result:** 3
**Explanation:** The array after merging 'a' and 'b' will be { 1, 2, 3, 4, 6 }. The median is simply 3.

# Optimal Solution

```Javascript

function median(a, b) {
    let n1 = a.length, n2 = b.length;
    // if n1 is bigger swap the arrays:
    if (n1 > n2) return median(b, a);

    let n = n1 + n2; // total length
    let left = Math.floor((n1 + n2 + 1) / 2); // length of left half
    // apply binary search:
    let low = 0, high = n1;
    while (low <= high) {
        let mid1 = Math.floor((low + high) / 2);
        let mid2 = left - mid1;
        // calculate l1, l2, r1, and r2
        let l1 = Number.MIN_SAFE_INTEGER, l2 = Number.MIN_SAFE_INTEGER;
        let r1 = Number.MAX_SAFE_INTEGER, r2 = Number.MAX_SAFE_INTEGER;
        if (mid1 < n1) r1 = a[mid1];
        if (mid2 < n2) r2 = b[mid2];
        if (mid1 - 1 >= 0) l1 = a[mid1 - 1];
        if (mid2 - 1 >= 0) l2 = b[mid2 - 1];

        if (l1 <= r2 && l2 <= r1) {
            if (n % 2 === 1) return Math.max(l1, l2);
            else return (Math.max(l1, l2) + Math.min(r1, r2)) / 2;
        }

        // eliminate the halves:
        else if (l1 > r2) high = mid1 - 1;
        else low = mid1 + 1;
    }
    return 0; // dummy statement
}

let a = [1, 4, 7, 10, 12];
let b = [2, 3, 6, 15];
console.log("The median of two sorted arrays is " + median(a, b).toFixed(1));

```

**Time Complexity:** O(log(min(n1,n2))), where n1 and n2 are the sizes of two given arrays.  
**Reason:** We are applying binary search on the range [0, min(n1, n2)].

**Space Complexity:** O(1) as no extra space is used.