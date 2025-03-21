# **Problem statement:** 
You are given a sorted array of integers and a target, your task is to search for the target in the given array. Assume the given array does not contain any duplicate numbers.

Let’s say the given array is = {3, 4, 6, 7, 9, 12, 16, 17} and target = 6.

## **Recursive implementation:**

```Javascript
function binarySearch(nums, low, high, target) {
    if (low > high) return -1; // Base case.

    // Perform the steps:
    let mid = Math.floor((low + high) / 2);
    if (nums[mid] === target) return mid;
    else if (target > nums[mid])
        return binarySearch(nums, mid + 1, high, target);
    return binarySearch(nums, low, mid - 1, target);
}

function search(nums, target) {
    return binarySearch(nums, 0, nums.length - 1, target);
}

let a = [3, 4, 6, 7, 9, 12, 16, 17];
let target = 6;
let ind = search(a, target);
if (ind === -1) console.log("The target is not present.");
else console.log("The target is at index:", ind);


```

## **Time Complexity:**

In the algorithm, in every step, we are basically dividing the search space into 2 equal halves. This is actually equivalent to dividing the size of the array by 2, every time. After a certain number of divisions, the size will reduce to such an extent that we will not be able to divide that anymore and the process will stop. The number of total divisions will be equal to the time complexity.

Let’s derive the number of divisions mathematically,

If a number n can be divided by 2 for x times:
	2^x = n
Therefore, x = logn (base is 2)

So the overall time complexity is O(logN), where N = size of the given array.