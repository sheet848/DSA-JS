The **Candy Problem** is a common greedy algorithm problem. The goal is to distribute candies to children standing in a line such that:

1. Each child gets at least one candy.
2. A child with a higher rating than their neighbor gets more candies than their neighbor.

We aim to minimize the total number of candies distributed while satisfying these conditions.

---

### **Greedy Algorithm Solution**:

The optimal solution involves two passes through the ratings:

1. In the first pass (left-to-right), ensure that each child has more candies than their left neighbor if their rating is higher.
2. In the second pass (right-to-left), ensure that each child has more candies than their right neighbor if their rating is higher.

---

### **JavaScript Implementation**:

```javascript
function candy(ratings) {
    const n = ratings.length;
    const candies = new Array(n).fill(1);

    // First pass: left to right
    for (let i = 1; i < n; i++) {
        if (ratings[i] > ratings[i - 1]) {
            candies[i] = candies[i - 1] + 1;
        }
    }

    // Second pass: right to left
    for (let i = n - 2; i >= 0; i--) {
        if (ratings[i] > ratings[i + 1]) {
            candies[i] = Math.max(candies[i], candies[i + 1] + 1);
        }
    }

    // Calculate the total number of candies
    return candies.reduce((a, b) => a + b, 0);
}

// Example usage:
const ratings = [1, 0, 2];
console.log("Minimum candies required:", candy(ratings));
```

---

### **Explanation**:

1. **Initialization**:
    - Each child starts with 1 candy (the minimum required).
2. **Left-to-Right Pass**:
    - If a child’s rating is higher than the one on their left, they get one more candy than the left neighbor.
3. **Right-to-Left Pass**:
    - If a child’s rating is higher than the one on their right, they get one more candy than the right neighbor, while keeping the maximum of the two conditions.
4. **Result**:
    - Sum up the candies to get the minimum number of candies distributed.

---

### **Example**:

For `ratings = [1, 0, 2]`:

- **Left-to-Right Pass**:
    - Candies = `[1, 1, 2]`
- **Right-to-Left Pass**:
    - Candies = `[2, 1, 2]`
- Total candies = `2 + 1 + 2 = 5`.

---

### **Time Complexity**:

- **O(n)** for two passes (left-to-right and right-to-left).

### **Space Complexity**:

- **O(n)** for the `candies` array.

This greedy algorithm ensures an optimal solution for distributing candies while meeting the problem constraints. Let me know if you'd like to explore any variations!