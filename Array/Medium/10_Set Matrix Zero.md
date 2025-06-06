# Problem Statement
**Examples 1:****Input:** matrix=[[1,1,1],[1,0,1],[1,1,1]]

**Output:** [[1,0,1],[0,0,0],[1,0,1]]

**Explanation:** Since matrix[2][2]=0.Therfore the 2nd column and 2nd row wil be set to 0.
 
**Input:** matrix=[[0,1,2,0],[3,4,5,2],[1,3,1,5]]

**Output:**[[0,0,0,0],[0,4,5,0],[0,3,1,0]]

**Explanation:**Since matrix[0][0]=0 and matrix[0][3]=0. Therefore 1st row, 1st column and 4th column will be set to 0

## Optimal Approach

```

function zeroMatrix(matrix) {
    const n = matrix.length;
    const m = matrix[0].length;

    let col0 = 1;
    // Step 1: Traverse the matrix and mark 1st row & col accordingly:
    for (let i = 0; i < n; i++) {
        for (let j = 0; j < m; j++) {
            if (matrix[i][j] === 0) {
                // Mark i-th row:
                matrix[i][0] = 0;

                // Mark j-th column:
                if (j !== 0) {
                    matrix[0][j] = 0;
                } else {
                    col0 = 0;
                }
            }
        }
    }

    // Step 2: Mark with 0 from (1,1) to (n-1, m-1):
    for (let i = 1; i < n; i++) {
        for (let j = 1; j < m; j++) {
            if (matrix[i][j] !== 0) {
                // Check for col & row:
                if (matrix[i][0] === 0 || matrix[0][j] === 0) {
                    matrix[i][j] = 0;
                }
            }
        }
    }

    // Step 3: Finally mark the 1st col & then 1st row:
    if (matrix[0][0] === 0) {
        for (let j = 0; j < m; j++) {
            matrix[0][j] = 0;
        }
    }
    if (col0 === 0) {
        for (let i = 0; i < n; i++) {
            matrix[i][0] = 0;
        }
    }

    return matrix;
}

const matrix = [[1, 1, 1], [1, 0, 1], [1, 1, 1]];
const ans = zeroMatrix(matrix);

console.log("The Final matrix is:");
for (const row of ans) {
    console.log(row.join(" "));
}    

```
**Time Complexity:** O(2*(N*M))
**Space Complexity:** O(1)
