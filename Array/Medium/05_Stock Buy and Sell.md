# Problem Statement
**Example 1:****Input:** prices = [7,1,5,3,6,4]
**Output:** 5
**Explanation:** Buy on day 2 (price = 1) and 
sell on day 5 (price = 6), profit = 6-1 = 5.

**Note**: That buying on day 2 and selling on day 1 
is not allowed because you must buy before 
you sell.

**Example 2:****Input:** prices = [7,6,4,3,1]
**Output:** 0
**Explanation:** In this case, no transactions are 
done and the max profit = 0.

## Optimal Approach

```
const maxProfit = (arr) => {
  let maxPro = 0;
  let minPrice = Number.MAX_VALUE;

  for (let i = 0; i < arr.length; i++) {
    minPrice = Math.min(minPrice, arr[i]);
    maxPro = Math.max(maxPro, arr[i] - minPrice);
  }

  return maxPro;
}

const arr = [7,1,5,3,6,4];
const maxPro = maxProfit(arr);
console.log("Max profit is: ", maxPro);
```

**Time complexity:** O(n)
**Space Complexity:** O(1)
