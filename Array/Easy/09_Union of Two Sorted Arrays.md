
## Solution 3 : Two Pointers

```
function findUnion(arr1, arr2) {
  let i = 0, j = 0; // Pointers
  let union = []; // Union array

  while (i < arr1.length && j < arr2.length) {
    if (arr1[i] <= arr2[j]) { // Case 1 and 2
      if (union.length === 0 || union[union.length - 1] !== arr1[i])
        union.push(arr1[i]);
      i++;
    } else { // Case 3
      if (union.length === 0 || union[union.length - 1] !== arr2[j])
        union.push(arr2[j]);
      j++;
    }
  }

  while (i < arr1.length) { // If any elements left in arr1
    if (union[union.length - 1] !== arr1[i])
      union.push(arr1[i]);
    i++;
  }

  while (j < arr2.length) { // If any elements left in arr2
    if (union[union.length - 1] !== arr2[j])
      union.push(arr2[j]);
    j++;
  }

  return union;
}

const arr1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const arr2 = [2, 3, 4, 4, 5, 11, 12];

const union = findUnion(arr1, arr2);

console.log("Union of arr1 and arr2 is:");
console.log(union.join(" "));

```

**Time Complexity**: O(m+n)
**Space Complexity : O(m+n)** {If Space of Union ArrayList is considered} 
**O(1)** {If Space of union ArrayList is not considered}

