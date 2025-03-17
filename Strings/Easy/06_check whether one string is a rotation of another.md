To check whether one string is a rotation of another, you can use the idea that a rotated version of a string is always a substring of the original string concatenated with itself. Here's how you can implement this in JavaScript:

### JavaScript Code:

```Javascript
function isRotation(s1, s2) {
    if (s1.length !== s2.length) return false; // Rotations must have the same length

    // Concatenate the string with itself and check if s2 is a substring
    const concatenated = s1 + s1;
    return concatenated.includes(s2);
}

// Example Usage
let s1 = "waterbottle";
let s2 = "erbottlewat";
console.log(isRotation(s1, s2)); // Output: true

s1 = "hello";
s2 = "ollhe";
console.log(isRotation(s1, s2)); // Output: false
```

### Explanation:

1. **Check Lengths**:
    
    - If the lengths of the two strings are not the same, they cannot be rotations of each other.
        
2. **Concatenation**:
    
    - Concatenate `s1` with itself. For example, if `s1 = "waterbottle"`, then `s1 + s1 = "waterbottlewaterbottle"`.
        
    - A rotated version of `s1` (e.g., `"erbottlewat"`) will always appear as a substring within this concatenated string.
        
3. **Check Substring**:
    
    - Use the `includes` function to check if `s2` is a substring of the concatenated string.
        

This solution works efficiently in **O(n)** time, where `n` is the length of the strings, and it uses only a small amount of additional space. Let me know if you'd like further clarification!