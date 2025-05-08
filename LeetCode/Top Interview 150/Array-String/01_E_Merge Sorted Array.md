You can solve this efficiently in-place using the two-pointer technique, starting from the end of both arrays. Since nums1 has enough space to hold all elements of both arrays, we fill it from the back to avoid overwriting values we still need to compare.

```
var merge = function(nums1, m, nums2, n) {
    let p1 = m - 1;
    let p2 = n - 1;
    let p = m + n - 1;

    while (p1 >=0 && p2 >= 0) {
        if(nums1[p1] > nums2[p2]) {
            nums1[p] = nums1[p1];
            p1--;
        } else {
            nums1[p] = nums2[p2];
            p2--;
        }
        p--;
    }

    while (p2 >= 0) {
        nums1[p] = nums2[p2];
        p2--;
        p--;
    }
};
```
```
let nums1 = [1, 2, 3, 0, 0, 0];
let m = 3;
let nums2 = [2, 5, 6];
let n = 3;

merge(nums1, m, nums2, n);

console.log(nums1); // Output: [1, 2, 2, 3, 5, 6]
```

This approach runs in O(m + n) time and uses O(1) extra space.
