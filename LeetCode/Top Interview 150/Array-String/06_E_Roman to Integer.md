To convert a Roman numeral to an integer, you scan the string from left to right:

If the current value is less than the next, subtract it.

Otherwise, add it.

```
function romanToInt(s) {
    const roman = {
        'I': 1, 'V': 5, 'X': 10,
        'L': 50, 'C': 100,
        'D': 500, 'M': 1000
    };

    let total = 0;

    for (let i = 0; i < s.length; i++) {
        const curr = roman[s[i]];
        const next = roman[s[i + 1]];

        if (next > curr) {
            total += next - curr;
            i++; // Skip next character
        } else {
            total += curr;
        }
    }

    return total;
}

```
```
console.log(romanToInt("III"));    // Output: 3
console.log(romanToInt("IV"));     // Output: 4
console.log(romanToInt("IX"));     // Output: 9
console.log(romanToInt("LVIII"));  // Output: 58
console.log(romanToInt("MCMXCIV"));// Output: 1994

```

## Time and Space Complexity:
Time: O(n), where n is the length of the Roman numeral string

Space: O(1), constant dictionary
