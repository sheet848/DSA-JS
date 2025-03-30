**Example 1:**

**Input:** x = 2.00000, n = 10

**Output:** 1024.00000

**Explanation:** You need to calculate 2.00000 raised to 10 which gives ans 1024.00000

**Example 2:**

**Input:** x = 2.10000, n = 3

**Output:** 9.26100

**Explanation:** You need to calculate 2.10000 raised to 3 which gives ans 9.26100

## Solution

Here's an optimal solution to implement `Pow(x, n)` in JavaScript using recursion and divide-and-conquer principles:

```javascript
function myPow(x, n) {
    if (n === 0) {
        return 1; // Base case: anything raised to the power of 0 is 1
    }
    
    if (n < 0) {
        x = 1 / x; // Handle negative powers
        n = -n;
    }
    
    if (n % 2 === 0) {
        let half = myPow(x, n / 2);
        return half * half; // Efficiently square the result for even exponents
    } else {
        return x * myPow(x, n - 1); // Multiply by x for odd exponents
    }
}

// Example usage:
console.log(myPow(2, 10)); // Output: 1024
console.log(myPow(2, -2)); // Output: 0.25
```

### Explanation:

1. **Base Case**: When the exponent (`n`) is `0`, the result is always `1`.
2. **Negative Powers**: Convert the problem to its reciprocal, i.e., (x^{-n} = 1 / x^n).
3. **Divide-and-Conquer**:
    - If `n` is even, recursively compute (x^{n/2}) and square the result to reduce computation.
    - If `n` is odd, reduce it to (x^{n-1}) and multiply by `x`.

This approach ensures optimal time complexity of (O(\log n)) due to the halving of the exponent in each step. It's both efficient and elegant!