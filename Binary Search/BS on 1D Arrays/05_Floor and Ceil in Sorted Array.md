# Problem Statement

## **Problem Statement:** 

You're given an sorted array arr of n integers and an integer x. Find the floor and ceiling of x in arr[0..n-1].  
The floor of x is the largest element in the array which is smaller than or equal to x.  
The ceiling of x is the smallest element in the array greater than or equal to x.

**Example 1:**
**Input Format:** n = 6, arr[] ={3, 4, 4, 7, 8, 10}, x= 5
**Result:** 4 7
**Explanation:** The floor of 5 in the array is 4, and the ceiling of 5 in the array is 7.

**Example 2:**
**Input Format:** n = 6, arr[] ={3, 4, 4, 7, 8, 10}, x= 8
**Result:** 8 8
**Explanation:** The floor of 8 in the array is 8, and the ceiling of 8 in the array is also 8.

_The primary objective of the Binary Search algorithm is to efficiently determine the appropriate half to eliminate, thereby reducing the search space by half. It does this by determining a specific condition that ensures that the target is not present in that half._

# Solution

```Javascript

function findFloorAndCeil(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    let floor = -1; // Default if no floor exists
    let ceil = -1;  // Default if no ceil exists

    while (left <= right) {
        const mid = Math.floor((left + right) / 2);

        if (nums[mid] === target) {
            // Target exactly matches; both floor and ceil are the same
            return { floor: nums[mid], ceil: nums[mid] };
        } else if (nums[mid] < target) {
            // Update floor and move to the right half
            floor = nums[mid];
            left = mid + 1;
        } else {
            // Update ceil and move to the left half
            ceil = nums[mid];
            right = mid - 1;
        }
    }

    return { floor, ceil };
}

// Example Usage
const nums = [1, 3, 5, 7, 9];
const target = 6;

console.log(findFloorAndCeil(nums, target)); // Output: { floor: 5, ceil: 7 }
console.log(findFloorAndCeil(nums, 10));     // Output: { floor: 9, ceil: -1 }
console.log(findFloorAndCeil(nums, 0));      // Output: { floor: -1, ceil: 1 }
console.log(findFloorAndCeil(nums, 5));      // Output: { floor: 5, ceil: 5 }

```

---
### **How It Works**

1. **Binary Search Logic:**
    
    - Calculate the middle index: `mid = Math.floor((left + right) / 2)`.
        
    - If `nums[mid] < target`, update `floor` and move the `left` pointer.
        
    - If `nums[mid] > target`, update `ceil` and move the `right` pointer.
        
    - If `nums[mid] === target`, the `floor` and `ceil` are both equal to the target.
        
2. **Return Values:**
    
    - If no floor exists, `floor` remains `-1`.
        
    - If no ceil exists, `ceil` remains `-1`.
        

### **Edge Cases**

1. **Empty Array:** Return `{ floor: -1, ceil: -1 }`.
    
2. **Target Smaller Than All Elements:** Only `ceil` will exist.
    
3. **Target Larger Than All Elements:** Only `floor` will exist.