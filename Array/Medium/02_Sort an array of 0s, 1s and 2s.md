# Problem Statement

**Input:** nums = [2,0,2,1,1,0]
**Output**: [0,0,1,1,2,2]

**Input:** nums = [2,0,1]
**Output:** [0,1,2]

**Input:** nums = [0]
**Output:** [0]
### Optimal Approach

**Dutch National Flag algorithm:**

```
function sortArray(arr) {
    let low = 0, mid = 0, high = arr.length - 1; // 3 pointers

    while (mid <= high) {
        if (arr[mid] === 0) {
            [arr[low], arr[mid]] = [arr[mid], arr[low]]; // swap 0s
            low++;
            mid++;
        } else if (arr[mid] === 1) {
            mid++;
        } else {
            [arr[mid], arr[high]] = [arr[high], arr[mid]]; // swap 2s
            high--;
        }
    }
}

// Example usage:
const arr = [0, 2, 1, 2, 0, 1];
sortArray(arr);
console.log("After sorting:");
console.log(arr.join(" ")); // Output: 0 0 1 1 2 2

```

**Time Complexity:** O(N)
**Space Complexity:** O(1)

---

## Dutch National Flag Algorithm

The Dutch National Flag algorithm is a sorting algorithm that was proposed by Edsger Dijkstra to solve the problem of sorting an array containing three distinct elements. It's named after the Dutch national flag, which consists of three horizontal bands in different colors.

The goal of the algorithm is to sort an array containing three distinct elements (like 0s, 1s, and 2s) in linear time and with a single pass through the array. Here's how it works:

1. **Three Pointers**: The algorithm uses three pointers: `low`, `mid`, and `high`.
    
    - `low` marks the boundary of the sub-array containing 0s.
        
    - `mid` is the current element being examined.
        
    - `high` marks the boundary of the sub-array containing 2s.
        
2. **Initialization**:
    
    - Set `low` and `mid` to the start of the array (index 0).
        
    - Set `high` to the end of the array (index `n-1`).
        
3. **Traversal**:
    
    - Traverse the array with `mid` until it exceeds `high`.
        
    - At each step, inspect the value at `arr[mid]`:
        
        - If `arr[mid]` is 0, swap `arr[low]` and `arr[mid]`, then increment both `low` and `mid`.
            
        - If `arr[mid]` is 1, just move `mid` to the next element.
            
        - If `arr[mid]` is 2, swap `arr[mid]` and `arr[high]`, then decrement `high` (without incrementing `mid`).
            
4. **Result**:
    
    - By the end of the traversal, all 0s will be at the beginning, all 1s will be in the middle, and all 2s will be at the end.
        

Here's a visualization of how the algorithm progresses:

|Step|Array|low|mid|high|
|---|---|---|---|---|
|Init|[0, 2, 1, 2, 0, 1]|0|0|5|
|1|[0, 2, 1, 2, 0, 1]|1|1|5|
|2|[0, 2, 1, 2, 0, 1]|1|1|4|
|3|[0, 1, 1, 2, 0, 2]|1|1|3|
|4|[0, 1, 1, 2, 0, 2]|1|2|3|
|5|[0, 1, 1, 0, 2, 2]|2|3|3|
|6|[0, 1, 1, 0, 2, 2]|2|4|2|
|End|[0, 1, 1, 0, 2, 2]|-|-|-|

The final sorted array will be: `[0, 0, 1, 1, 2, 2]`.

This algorithm is efficient with a time complexity of **O(n)** and a space complexity of **O(1)**, making it a great choice for sorting arrays with three distinct elements.