**Problem Statement:** Given two arrays representing children’s greed factor and cookie sizes, the goal is to maximise the number of content children.

Each child i has a greed factor of g[i], which is the minimum size of a cookie that will make the child content. Each cookie j has a size of s[j]. If s[j] >= g[j], we can assign cookie j to child i, making the child content. Each child can only receive one cookie.

**Example 1:**
**Input:**g = [1, 2, 3], s = [1, 1]
**Output:** 1
**Explanation: ** 
We have 3 children and 2 cookies. The greed factors of the 3 children are 1, 2, 3. The sizes of the 2 cookies are both 1. We can only make the child with greed factor 1 content. Hence, the output is 1.

**Example 2:**
**Input:**g = [1, 5, 3, 3, 4], s = [4, 2, 1, 2, 1, 3]
Output:** 0
**Explanation:** 
You have 5 children and 6 cookies. The greed factors of the 5 children are 1, 5, 3, 3, and 4. The sizes of the 6 cookies are 4, 2, 1, 2, 1, and 3.

1. The child with greed factor 1 can be satisfied with the cookie of size 1.
2. One child with greed factor 3 can be satisfied with the cookie of size 3.
3. One child with greed factor 4 can be satisfied with the cookie of size 4.

Hence, the output is 3.

# Solution

```Javascript

                            
// Function to find the maximum number of content children
function findContentChildren(greed, cookieSize) {
    // Get the size of the greed array
    let n = greed.length;

    // Get the size of the cookieSize array
    let m = cookieSize.length;

    // Sort the greed factors in ascending order
    greed.sort((a, b) => a - b);

    // Sort the cookie sizes in ascending order
    cookieSize.sort((a, b) => a - b);

    // Initialize pointers
    let l = 0; // Pointer for cookieSize array
    let r = 0; // Pointer for greed array

    // Initialize variable to count satisfied children
    let satisfiedChildren = 0;

    // Iterate while there are cookies and children left to consider
    while (l < m && r < n) {
        // If the current cookie can satisfy the current child's greed
        if (greed[r] <= cookieSize[l]) {
            // Move to the next child
            r++;
            // Increment count of satisfied children
            satisfiedChildren++;
        }
        // Move to the next cookie
        l++;
    }

    // Return the number of children that were satisfied
    return satisfiedChildren;
}

// Main function to test the findContentChildren function
function main() {
    let greed = [1, 5, 3, 3, 4];
    let cookieSize = [4, 2, 1, 2, 1, 3];

    console.log("Array Representing Greed: " + greed.join(" "));
    console.log("Array Representing Cookie Size: " + cookieSize.join(" "));

    let ans = findContentChildren(greed, cookieSize);

    console.log("No. of kids assigned cookies: " + ans);
}

// Call the main function to test the code
main();
                            
                        
```

**Time Complexity: O(N logN + M logM + M)** where N is the length of the greedy array, M is the length of the cookies array. To sort the greedy and cookies array, the complexity is O(N logN) and O(M logM).

1. After sorting, we iterate over the arrays at most M times as M is the total number of cookies.
2. Since each child and each cookie is considered at most once, the time complexity of this part is linear in terms of the size of the cookie array, which is O(M).

**Space Complexity: O(1)** as the algorithm uses only a constant amount of extra space regardless of the size of the input array. It does not require any additional data structures that scale with the input size.
