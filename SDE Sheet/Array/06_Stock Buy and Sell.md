# Solution

```Javascript
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