# Variation 1
In this case, we are given the row number r and the column number c, and we need to find out the element at position (r,c).

```Javascript

function nCr(n, r) {
    let res = 1;

    // calculating nCr:
    for (let i = 0; i < r; i++) {
        res = res * (n - i);
        res = res / (i + 1);
    }
    return res;
    }

    function pascalTriangle(r, c) {
    const element = nCr(r - 1, c - 1);
    return element;
}

const r = 5; // row number
const c = 3; // col number
const element = pascalTriangle(r, c);
console.log(`The element at position (${r},${c}) is: ${element}`);

```

**Time Complexity:** O(c), where c = given column number.  
**Reason:** We are running a loop for r times, where r is c-1.

**Space Complexity:** O(1) as we are not using any extra space.

# Variation 2
**Given the row number n. Print the n-th row of Pascal’s triangle.**

```Javascript

function pascalTriangle(n) {
    let ans = 1;
    console.log(ans + " "); // printing 1st element
  
    //Printing the rest of the part:
    for (let i = 1; i < n; i++) {
      ans = ans * (n - i);
      ans = ans / i;
      console.log(ans + " ");
    }
    console.log("n");
}
  
const n = 5;
pascalTriangle(n);
        
```

**Time Complexity:** O(N) where N = given row number. Here we are using only a single loop.

**Space Complexity:** O(1) as we not using any extra space.

# Variation 3
Given the number of rows n. Print the first n rows of Pascal’s triangle.

```Javascript

function generateRow(row) {
    let ans = 1;
    let ansRow = [1]; // inserting the 1st element
  
    // calculate the rest of the elements:
    for (let col = 1; col < row; col++) {
      ans = ans * (row - col);
      ans = ans / col;
      ansRow.push(ans);
    }
    return ansRow;
}
  
function pascalTriangle(n) {
    let ans = [];

    // store the entire pascal's triangle:
    for (let row = 1; row <= n; row++) {
        ans.push(generateRow(row));
    }
    return ans;
}
  
let n = 5;
let ans = pascalTriangle(n);
for (let i = 0; i < ans.length; i++) {
    console.log(ans[i].join(" "));
}

```

**Time Complexity:** O(n2), where n = number of rows(given).  
**Reason:** We are generating a row for each single row. The number of rows is n. And generating an entire row takes O(n) time complexity.

**Space Complexity:** In this case, we are only using space to store the answer. That is why space complexity can still be considered as O(1).