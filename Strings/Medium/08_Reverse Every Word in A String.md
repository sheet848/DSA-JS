Here’s a simple and efficient way to reverse every word in a string using JavaScript:

```javascript
function reverseWords(s) {
    return s.split(' ') // Split the string into words
            .map(word => word.split('').reverse().join('')) // Reverse each word
            .join(' '); // Join the reversed words back into a string
}

// Example Usage:
const input = "Hello World";
console.log(reverseWords(input));
// Output: "olleH dlroW"
```

### Explanation:
1. **Split the String**:
   - Use `split(' ')` to break the string into an array of words based on spaces.
2. **Reverse Each Word**:
   - Use `.map()` to process each word in the array.
   - Reverse the characters in each word using `split('')` (to split into characters), `reverse()` (to reverse the array), and `join('')` (to rejoin them into a string).
3. **Rejoin Words**:
   - Use `join(' ')` to combine the reversed words back into a single string with spaces.

### Efficiency:
- **Time Complexity**: **O(n)**, where `n` is the total number of characters in the string (processing each word and reversing its characters).
- **Space Complexity**: **O(n)** for the temporary arrays used during splitting and reversing.

This method is clean, concise, and handles edge cases like multiple spaces or empty strings. Let me know if you'd like to explore more variations or use cases!