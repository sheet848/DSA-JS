# Problem Statement
**Example 1 :**

**Input format:** Arr[] = {1,3,2}
**Output**: Arr[] = {2,1,3}
**Explanation:** All permutations of {1,2,3} are {{1,2,3} , {1,3,2}, {2,13} , {2,3,1} , {3,1,2} , {3,2,1}}. So, the next permutation just after {1,3,2} is {2,1,3}.

**Example 2:**

**Input format:** Arr[] = {3,2,1}
**Output:** Arr[] = {1,2,3}
**Explanation:** As we see all permutations of {1,2,3}, we find {3,2,1} at the last position. So, we have to return the topmost permutation.

## Optimal Approach - breakpoint

```

function nextGreaterPermutation(A) {
    let n = A.length; // size of the array.

    // Step 1: Find the break point:
    let ind = -1; // break point
    for (let i = n - 2; i >= 0; i--) {
        if (A[i] < A[i + 1]) {
            // index i is the break point
            ind = i;
            break;
        }
    }

    // If break point does not exist:
    if (ind == -1) {
        // reverse the whole array:
        A.reverse();
        return A;
    }

    // Step 2: Find the next greater element
    //         and swap it with A[ind]:

    for (let i = n - 1; i > ind; i--) {
        if (A[i] > A[ind]) {
            [A[i], A[ind]] = [A[ind], A[i]]; // swap A[i] and A[ind]
            break;
        }
    }

    // Step 3: reverse the right half:
    A.splice(ind + 1, n - ind - 1, ...A.slice(ind + 1).reverse());

    return A;
}

let A = [2, 1, 5, 4, 3, 0, 0];
let ans = nextGreaterPermutation(A);

console.log("The next permutation is: [" + ans.join(" ") + "]");

```

**Time Complexity:** O(3N)
**Space Complexity:** O(1)
