To solve the problem of maximizing profit from buying and selling stock once, you need to find the maximum difference between two elements, where the larger element comes after the smaller one.

```
function maxProfit(prices) {
    let minPrice = Infinity;
    let maxProfit = 0;

    for (let price of prices) {
        if (price < minPrice) {
            minPrice = price; // Update to lower buy price
        } else {
            maxProfit = Math.max(maxProfit, price - minPrice); // Check potential profit
        }
    }

    return maxProfit;
}

```

```
let prices = [7, 1, 5, 3, 6, 4];
console.log(maxProfit(prices)); // Output: 5 (Buy at 1, sell at 6)
```

Time and Space Complexity:
Time: O(n)

Space: O(1)
