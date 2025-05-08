To find the majority element (the element that appears more than ⌊n / 2⌋ times), the most efficient solution is the Boyer-Moore Voting Algorithm.

```
function majorityElement(nums) {
    let count = 0;
    let candidate = null;

    for (let num of nums) {
        if (count === 0) {
            candidate = num;
        }
        count += (num === candidate) ? 1 : -1;
    }

    return candidate;
}

```
```
let nums = [2, 2, 1, 1, 1, 2, 2];
console.log(majorityElement(nums)); // Output: 2

```

Time: O(n)

Space: O(1)

This algorithm works under the assumption that a majority element always exists.
