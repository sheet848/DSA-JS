# Problem Statement

**Example 1:****Input Format**: N = 3, nums[] = {3,2,3}
**Result**: 3
**Explanation**: When we just count the occurrences of each number and compare with half of the size of the array, you will get 3 for the above solution. 

**Example 2:****Input Format:**  N = 7, nums[] = {2,2,1,1,1,2,2}

**Result**: 2

**Explanation**: After counting the number of times each element appears and comparing it with half of array size, we get 2 as result.

**Example 3:****Input Format:**  N = 10, nums[] = {4,4,2,4,3,4,4,3,2,4}

**Result**: 4
### Optimal Approach

 **Moore’s Voting Algorithm:**
```
function majorityElement(arr) {
    // Size of the given array
    let n = arr.length;
    let cnt = 0; // Count
    let el; // Element

    // Applying the algorithm
    for (let i = 0; i < n; i++) {
        if (cnt === 0) {
            cnt = 1;
            el = arr[i];
        } else if (el === arr[i]) {
            cnt++;
        } else {
            cnt--;
        }
    }

    // Checking if the stored element is the majority element
    let cnt1 = 0;
    for (let i = 0; i < n; i++) {
        if (arr[i] === el) {
            cnt1++;
        }
    }

    if (cnt1 > Math.floor(n / 2)) {
        return el;
    }
    return -1;
}

let arr = [2, 2, 1, 1, 1, 2, 2];
let ans = majorityElement(arr);
console.log("The majority element is:", ans);

```

**Time Complexity:** O(N) + O(N)
**Space Complexity:** O(1)

---

## **Moore’s Voting Algorithm:**

Moore's Voting Algorithm is a popular algorithm for finding the majority element in an array. A majority element is one that appears more than half the time in the array. The algorithm works in two main phases:

1. **Finding a Candidate**: In this phase, the algorithm tries to find a candidate that could potentially be the majority element.
    
2. **Verification**: In this phase, the algorithm verifies if the candidate is indeed the majority element.
    

Here is how the algorithm works:

1. **Initialization**:
    
    - Initialize `candidate` as `None`.
        
    - Initialize `count` as `0`.
        
2. **Finding a Candidate**:
    
    - Traverse through each element in the array.
        
    - If `count` is `0`, set `candidate` to the current element and set `count` to `1`.
        
    - If `count` is not `0` and the current element is the same as `candidate`, increment `count`.
        
    - If `count` is not `0` and the current element is different from `candidate`, decrement `count`.
        
3. **Verification**:
    
    - Reset `count` to `0`.
        
    - Traverse through the array again and count the occurrences of the `candidate`.
        
    - If the `count` of `candidate` is more than half the size of the array, `candidate` is the majority element. Otherwise, there is no majority element.