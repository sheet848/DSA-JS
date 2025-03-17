To check if two strings are anagrams of each other, we can compare the character counts in both strings. Here's a solution in JavaScript:

### JavaScript Code:
```javascript
function areAnagrams(s1, s2) {
    if (s1.length !== s2.length) return false; // Anagrams must have the same length

    const charCount = {};

    // Count characters in the first string
    for (const char of s1) {
        charCount[char] = (charCount[char] || 0) + 1;
    }

    // Subtract character counts using the second string
    for (const char of s2) {
        if (!charCount[char]) {
            return false; // Character is either missing or appears too many times
        }
        charCount[char]--;
    }

    return true; // All characters matched
}

// Example Usage
let s1 = "listen";
let s2 = "silent";
console.log(areAnagrams(s1, s2)); // Output: true

s1 = "hello";
s2 = "world";
console.log(areAnagrams(s1, s2)); // Output: false
```

### Explanation:
1. **Equal Length Check**:
   - If the lengths of the two strings are not the same, they can't be anagrams.

2. **Character Counting**:
   - Use a `charCount` object to track the frequency of each character in the first string.

3. **Validation with the Second String**:
   - For each character in the second string, decrement the count in `charCount`. If a character doesn't exist or has been used up, the strings are not anagrams.

4. **Final Check**:
   - If all character counts reach `0`, the strings are anagrams.

This solution has a time complexity of **O(n)**, where `n` is the length of the strings, as it iterates through the strings only once. Let me know if you'd like any alternative approaches or further explanation! 