You can solve this by in-place filtering using a pointer to overwrite elements that aren't equal to val.

```
function removeElement(nums, val) {
    let k = 0; // Index to overwrite valid elements

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== val) {
            nums[k] = nums[i]; // Overwrite at position k
            k++;
        }
    }

    return k; // Number of elements not equal to val
}
```
```
let nums = [3, 2, 2, 3];
let val = 3;

let k = removeElement(nums, val);

console.log(k);        // Output: 2
console.log(nums);     // Output: [2, 2, _, _] (values after index k are ignored)
```

The first k elements in nums are the valid result.

Elements after k can be any value and are irrelevant.

This runs in O(n) time and uses O(1) space.
