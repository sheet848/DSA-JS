Here’s the most optimal solution in JavaScript to sort characters by frequency:

```javascript
function frequencySort(s) {
    // Create a frequency map
    const freqMap = new Map();
    for (const char of s) {
        freqMap.set(char, (freqMap.get(char) || 0) + 1);
    }

    // Sort characters by frequency and build the result string
    return Array.from(freqMap)
        .sort((a, b) => b[1] - a[1]) // Sort by frequency in descending order
        .map(([char, freq]) => char.repeat(freq)) // Repeat characters by their frequency
        .join(""); // Combine all characters into a single string
}

// Example Usage
let input = "tree";
console.log(frequencySort(input)); // Output: "eert" or "eetr"
```

### Explanation:
1. **Frequency Map**:
   - Use a `Map` to store each character as a key and its frequency as the value.
2. **Sorting**:
   - Convert the map to an array, sort the entries by frequency (`b[1] - a[1]`) in descending order.
3. **Build the Result**:
   - Use `map()` to repeat each character by its frequency and then join the result into a single string.

This solution has a time complexity of **O(n log n)** due to the sorting step, where `n` is the length of the string. It’s optimal for this problem and ensures both efficiency and readability.