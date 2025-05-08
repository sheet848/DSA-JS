To remove duplicates from a sorted array in-place, you can use the two-pointer technique:

One pointer (i) tracks the position of the last unique element.

The other pointer (j) scans through the array.

```
function removeDuplicates(nums) {
    if (nums.length === 0) return 0;

    let i = 0; // Points to the last unique element

    for (let j = 1; j < nums.length; j++) {
        if (nums[j] !== nums[i]) {
            i++;
            nums[i] = nums[j]; // Move unique element forward
        }
    }

    return i + 1; // Length of array with unique elements
}

```

```
let nums = [1, 1, 2, 3, 3];
let k = removeDuplicates(nums);

console.log(k);        // Output: 3
console.log(nums);     // Output: [1, 2, 3, _, _] (first k elements are unique)

```

Time Complexity: O(n)

Space Complexity: O(1) (in-place)
