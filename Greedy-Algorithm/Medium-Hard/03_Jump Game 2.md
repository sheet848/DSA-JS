To solve the **Jump Game 2** problem optimally, where the goal is to reach the last index of the array in the minimum number of jumps, we can use the **Greedy Algorithm**. Here's the JavaScript implementation:

---

### **Greedy Solution**:

```javascript
function jump(nums) {
    let jumps = 0; // Number of jumps made
    let currentEnd = 0; // Farthest point reachable with current jumps
    let farthest = 0; // Farthest point reachable overall

    for (let i = 0; i < nums.length - 1; i++) {
        farthest = Math.max(farthest, i + nums[i]); // Update the farthest point reachable

        // When we reach the end of the current jump range
        if (i === currentEnd) {
            jumps++; // Increment jump count
            currentEnd = farthest; // Set new range end
        }
    }

    return jumps;
}

// Example usage:
const nums = [2, 3, 1, 1, 4];
console.log("Minimum jumps to reach the end:", jump(nums));
```

---

### **Explanation**:

1. **Initialization**:
    
    - `jumps` keeps track of the number of jumps made.
    - `currentEnd` marks the range (maximum index) reachable with the current number of jumps.
    - `farthest` keeps track of the farthest index reachable overall.
2. **Iterate Through the Array**:
    
    - For each index `i`, update the `farthest` point reachable using `i + nums[i]`.
    - If `i` reaches `currentEnd`, it means we've used a jump to cover the current range, so increment `jumps` and update `currentEnd` to `farthest`.
3. **Optimality**:
    
    - The algorithm uses a greedy approach to always jump as far as possible while ensuring minimal jumps.

---

### **Example Walkthrough**:

For `nums = [2, 3, 1, 1, 4]`:

- Start at index 0 (value 2).
- First jump reaches index 1 or 2.
- Second jump reaches the end (index 4).

Output: `2 jumps`.

---

### **Time Complexity**:

- **O(n)**: Single pass through the array.

### **Space Complexity**:

- **O(1)**: No additional data structures used.

This solution is highly efficient and works well for large arrays. Let me know if you'd like further clarification or more examples!