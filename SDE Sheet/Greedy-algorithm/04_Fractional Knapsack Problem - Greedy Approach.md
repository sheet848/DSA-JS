**Problem Statement:** The weight of **N** items and their corresponding values are given. We have to put these items in a knapsack of weight **W** such that the **total value** obtained is **maximized.**

**Note:** We can either take the item as a whole or break it into smaller units.

# Solution

The **Fractional Knapsack Problem** is a classic problem in optimization. The goal is to maximize the total value in a knapsack by selecting items in fractional amounts, subject to a weight limit. It is solved efficiently using the **Greedy Approach**.

---

### **Greedy Solution**:

#### **Steps**:

1. **Calculate Value per Unit Weight**:
    - For each item, calculate the "value density" (value/weight ratio).
2. **Sort Items**:
    - Sort the items in decreasing order of their value density.
3. **Pick Items**:
    - Start with the item having the highest value density and add as much of it as possible to the knapsack.
    - Move to the next item until the knapsack is full or all items are considered.

#### **Implementation in JavaScript**:

Here’s how you can solve it programmatically:

```javascript
function fractionalKnapsack(weights, values, capacity) {
    // Create an array of items with their value density (value/weight)
    let items = weights.map((weight, index) => ({
        weight: weight,
        value: values[index],
        density: values[index] / weight
    }));

    // Sort items by value density in decreasing order
    items.sort((a, b) => b.density - a.density);

    let totalValue = 0; // Total value in the knapsack
    let remainingCapacity = capacity;

    // Iterate through the sorted items
    for (let item of items) {
        if (remainingCapacity === 0) break;

        if (item.weight <= remainingCapacity) {
            // Take the whole item
            totalValue += item.value;
            remainingCapacity -= item.weight;
        } else {
            // Take a fraction of the item to fill the remaining capacity
            totalValue += item.density * remainingCapacity;
            remainingCapacity = 0; // Knapsack is full
        }
    }

    return totalValue;
}

// Example Usage:
const weights = [10, 20, 30];
const values = [60, 100, 120];
const capacity = 50;

const maxValue = fractionalKnapsack(weights, values, capacity);
console.log("Maximum Value in Knapsack:", maxValue);
```

---

### **Explanation of Code**:

1. **Item Representation**:
    - Each item is represented by its weight, value, and value density.
2. **Sorting**:
    - The items are sorted by their value density in descending order.
3. **Selection**:
    - Items are added to the knapsack, either fully or fractionally, based on the remaining capacity.
4. **Final Value**:
    - The total value represents the maximum value the knapsack can hold.

---

### **Time Complexity**:

- Sorting items: **O(n log n)**.
- Adding items to the knapsack: **O(n)**.
- Overall: **O(n log n)**.

This greedy approach works because taking items with the highest value density first always leads to an optimal solution for the Fractional Knapsack Problem. Let me know if you'd like further details or have other questions!
