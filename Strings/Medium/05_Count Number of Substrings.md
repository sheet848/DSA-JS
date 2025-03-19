Here’s an optimal solution to count the number of substrings that satisfy a certain condition using JavaScript. I'll use an example where we need to count substrings with all unique characters (you can adapt it for other conditions).

### Counting Substrings with Unique Characters
This approach uses the sliding window technique for optimal performance:

```javascript
function countUniqueCharacterSubstrings(s) {
    let left = 0;
    let right = 0;
    const charSet = new Set();
    let count = 0;

    while (right < s.length) {
        if (!charSet.has(s[right])) {
            // Expand the window by including the current character
            charSet.add(s[right]);
            count += (right - left + 1); // Add all substrings ending at 'right'
            right++;
        } else {
            // Shrink the window by removing the leftmost character
            charSet.delete(s[left]);
            left++;
        }
    }

    return count;
}

// Example Usage:
const input = "abc";
console.log(countUniqueCharacterSubstrings(input));
// Output: 6
```

### Explanation:
1. **Sliding Window Technique**:
   - Use a `Set` to store characters in the current window.
   - Expand the window by moving `right` and adding new characters until a duplicate is encountered.
   - Shrink the window by moving `left` to remove characters and ensure all characters in the window are unique.
2. **Counting Substrings**:
   - When expanding the window, all substrings ending at `right` are valid and can be added to the count.
   - For each step, `count += (right - left + 1)` adds the substrings to the total.

### Efficiency:
- **Time Complexity**: **O(n)**, as each character is added and removed from the `Set` at most once.
- **Space Complexity**: **O(k)**, where `k` is the size of the character set (e.g., 26 for English lowercase letters).

If your condition for counting substrings is different (e.g., counting substrings with a certain sum, certain number of distinct characters, etc.), let me know—I can adapt this solution for your needs!