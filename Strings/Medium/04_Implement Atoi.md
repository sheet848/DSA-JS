Here’s an optimal implementation of the `Atoi` function in JavaScript. It converts a string to an integer while handling edge cases like invalid input, leading/trailing whitespace, and overflow:

```javascript
function myAtoi(s) {
    // Trim leading and trailing whitespaces
    s = s.trim();

    if (s.length === 0) return 0; // Handle empty string

    let index = 0, sign = 1, result = 0;

    // Determine the sign
    if (s[index] === '+' || s[index] === '-') {
        sign = (s[index] === '-') ? -1 : 1;
        index++;
    }

    // Parse digits
    while (index < s.length && s[index] >= '0' && s[index] <= '9') {
        result = result * 10 + (s[index] - '0');

        // Handle overflow (assuming 32-bit signed integers)
        if (result * sign > 2147483647) return 2147483647;
        if (result * sign < -2147483648) return -2147483648;

        index++;
    }

    return result * sign;
}

// Example Usage:
console.log(myAtoi("42"));           // Output: 42
console.log(myAtoi("   -42"));       // Output: -42
console.log(myAtoi("4193 with words")); // Output: 4193
console.log(myAtoi("words and 987"));   // Output: 0
console.log(myAtoi("-91283472332"));    // Output: -2147483648
```

### Explanation:
1. **Trimming Whitespace**: Use `trim()` to remove unnecessary leading and trailing whitespace.
2. **Sign Handling**: Check the first character for a `+` or `-` to determine the sign of the number.
3. **Parsing Digits**: Traverse the string and convert digits to an integer. Stop processing when encountering a non-digit character.
4. **Overflow**: Clamp the result to the limits of a 32-bit signed integer:
   - Maximum: `2147483647`
   - Minimum: `-2147483648`

### Efficiency:
- **Time Complexity**: **O(n)**, where `n` is the length of the string.
- **Space Complexity**: **O(1)**, as no additional space is used beyond a few variables.

This implementation should cover all the edge cases while remaining optimal. Let me know if you’d like to dive deeper into any part of the code!