Here are the optimal solutions for converting Roman numerals to integers and vice versa using JavaScript:

### Roman to Integer
This solution processes the string from left to right, checking for special subtraction cases like `IV` or `IX`:

```javascript
function romanToInt(s) {
    const romanMap = {
        'I': 1, 'V': 5, 'X': 10,
        'L': 50, 'C': 100, 'D': 500, 'M': 1000
    };

    let total = 0;

    for (let i = 0; i < s.length; i++) {
        const current = romanMap[s[i]];
        const next = romanMap[s[i + 1]];

        if (next && current < next) {
            // Subtraction case
            total -= current;
        } else {
            total += current;
        }
    }

    return total;
}

// Example Usage:
console.log(romanToInt("MCMXCIV")); // Output: 1994
```

### Integer to Roman
This solution maps integers to Roman numeral values and builds the result iteratively:

```javascript
function intToRoman(num) {
    const valueMap = [
        [1000, 'M'], [900, 'CM'], [500, 'D'], [400, 'CD'],
        [100, 'C'], [90, 'XC'], [50, 'L'], [40, 'XL'],
        [10, 'X'], [9, 'IX'], [5, 'V'], [4, 'IV'], [1, 'I']
    ];

    let roman = '';

    for (let [value, symbol] of valueMap) {
        while (num >= value) {
            roman += symbol;
            num -= value;
        }
    }

    return roman;
}

// Example Usage:
console.log(intToRoman(1994)); // Output: "MCMXCIV"
```

### Explanation:
1. **Roman to Integer**:
   - Use a map to store Roman numeral values.
   - Check for subtraction cases (e.g., `IV = 4`) by comparing the current value with the next.
   - If the current is smaller than the next, subtract it; otherwise, add it.

2. **Integer to Roman**:
   - Use a sorted list of integer-to-Roman mappings.
   - Iteratively subtract the largest possible value from the number while appending the corresponding Roman numeral.

### Efficiency:
Both solutions run efficiently:
- **Time Complexity**:
  - Roman to Integer: **O(n)**, where `n` is the length of the Roman numeral string.
  - Integer to Roman: **O(1)** due to the fixed set of Roman numeral rules.
- **Space Complexity**: **O(1)** for both, as only a fixed amount of auxiliary storage is used.

Let me know if you'd like more details or examples for either case!