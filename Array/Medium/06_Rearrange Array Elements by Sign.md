# Problem Statement
**Example 1**:

**Input**:
arr[] = {1,2,-4,-5}, N = 4
**Output**:
1 -4 2 -5

**Explanation**: 

Positive elements = 1,2
Negative elements = -4,-5
To maintain relative ordering, 1 must occur before 2, and -4 must occur before -5.

**Example 2**:
**Input**:
arr[] = {1,2,-3,-1,-2,-3}, N = 6
**Output:**
1 -3 2 -1 3 -2
**Explanation**: 

Positive elements = 1,2,3
Negative elements = -3,-1,-2
To maintain relative ordering, 1 must occur before 2, and 2 must occur before 3.
Also, -3 should come before -1, and -1 should come before -2.
## Optimal Approach
```
// Define a function to rearrange an array of integers by sign.
function RearrangebySign(A) {

  let n = A.length;

  // Define an array for storing the answer separately.
  let ans = new Array(n).fill(0);

  // Positive elements start from 0 and negative from 1.
  let posIndex = 0, negIndex = 1;
  for (let i = 0; i < n; i++) {

    // Fill negative elements in odd indices and increment by 2.
    if (A[i] < 0) {
      ans[negIndex] = A[i];
      negIndex += 2;
    }

    // Fill positive elements in even indices and increment by 2.
    else {
      ans[posIndex] = A[i];
      posIndex += 2;
    }
  }

  return ans;
}

// Define an array and call the RearrangebySign function.
let A = [1, 2, -4, -5];

let ans = RearrangebySign(A);

// Print the result.
console.log(ans.join(" "));
```
**Time Complexity:** O(N)
**Space Complexity:**  O(N)

# Problem Statement

**Example 1**:

**Input**:
arr[] = {1,2,-4,-5,3,4}, N = 6
**Output**:
1 -4 2 -5 3 4

**Explanation**: 

Positive elements = 1,2
Negative elements = -4,-5
To maintain relative ordering, 1 must occur before 2, and -4 must occur before -5.
Leftover positive elements are 3 and 4 which are then placed at the end of the array.

**Example 2:**
**Input:**
arr[] = {1,2,-3,-1,-2,-3}, N = 6
**Output:**
1 -3 2 -1 3 -2
**Explanation:** 

Positive elements = 1,2
Negative elements = -3,-1,-2,-4
To maintain relative ordering, 1 must occur before 2.
Also, -3 should come before -1, and -1 should come before -2.
After alternate ordering, -2 and -4 are left, which would be placed at the end of the ans array.

## Solution
```
function RearrangebySign(A) {
    
  let n = A.length;
  
  // Define 2 arrays, one for storing positive 
  // and other for negative elements of the array.
  let pos = [];
  let neg = [];
  
  // Segregate the array into positives and negatives.
  for(let i=0;i<n;i++){
      
      if(A[i]>0) pos.push(A[i]);
      else neg.push(A[i]);
  }
  
  // If positives are lesser than the negatives.
  if(pos.length < neg.length){
      
    // First, fill array alternatively till the point 
    // where positives and negatives are equal in number.
    for(let i=0;i<pos.length;i++){
      
      A[2*i] = pos[i];
      A[2*i+1] = neg[i];
    }
    
    // Fill the remaining negatives at the end of the array.
    let index = pos.length*2;
    for(let i = pos.length;i<neg.length;i++){
        
        A[index] = neg[i];
        index++;
    }
  }
  
  // If negatives are lesser than the positives.
  else{
      
      // First, fill array alternatively till the point 
      // where positives and negatives are equal in number.
      for(let i=0;i<neg.length;i++){
      
      A[2*i] = pos[i];
      A[2*i+1] = neg[i];
  }
    
    // Fill the remaining positives at the end of the array.
    let index = neg.length*2;
    for(let i = neg.length;i<pos.length;i++){
        
        A[index] = pos[i];
        index++;
    }
  }
  return A;
    
}

// Array Initialisation.
let A = [1,2,-4,-5,3,4];

let ans = RearrangebySign(A);

for (let i = 0; i < ans.length; i++) {
    console.log(ans[i]);
}
```

**Time Complexity:** O(2*N)
**Space Complexity:**  O(N/2 + N/2) = O(N)



