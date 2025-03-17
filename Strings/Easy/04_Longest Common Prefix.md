The "Longest Common Prefix" problem asks us to find the longest string that is a prefix (starting substring) of all the given strings in an array. Here's how you can solve this in JavaScript:

### JavaScript Code:

```Javascript
function longestCommonPrefix(strs) {
    if (strs.length === 0) return ""; // Handle edge case: empty array

    let prefix = strs[0]; // Assume the first string is the prefix

    for (let i = 1; i < strs.length; i++) {
        while (strs[i].indexOf(prefix) !== 0) {
            // Shrink the prefix until it's a prefix of strs[i]
            prefix = prefix.slice(0, -1);
            if (prefix === "") return ""; // No common prefix
        }
    }

    return prefix;
}

// Example Usage
let input = ["flower", "flow", "flight"];
console.log(longestCommonPrefix(input)); // Output: "fl"
```

### Explanation:

1. **Assume the first string is the common prefix**:
    
    - Start with the first string in the array (`prefix`).
        
2. **Iterate through the rest of the strings**:
    
    - Check if the current `prefix` is at the beginning of each string using `indexOf`.
        
    - If not, reduce the `prefix` by removing the last character (`slice(0, -1)`).
        
3. **Repeat until all strings match the prefix**:
    
    - If the `prefix` becomes empty, return `""` because no common prefix exists.
        
4. **Return the final prefix**.
    

This solution ensures we progressively shorten the prefix until it matches all the strings. The time complexity is **O(S)**, where `S` is the sum of all characters in the input strings, because in the worst case, we compare every character of every string.