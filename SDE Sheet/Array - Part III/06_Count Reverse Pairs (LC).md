**Problem Statement:** Given an array of numbers, you need to return the count of reverse pairs. **Reverse Pairs** are those pairs where i<j and arr[i]>2*arr[j].

**Example 1:****Input:** N = 5, array[] = {1,3,2,3,1)

**Output**: 2 

**Explanation:** The pairs are (3, 1) and (3, 1) as from both the pairs the condition arr[i] > 2*arr[j] is satisfied.

**Example 2:****Input:** N = 4, array[] = {3,2,1,4}

**Output:** 1

**Explaination:** There is only 1 pair  ( 3 , 1 ) that satisfy the condition arr[i] > 2*arr[j]

## Optimal Solution

```Javascript

function merge(arr, low, mid, high) {
  let temp = []; // temporary array
  let left = low; // starting index of left half of arr
  let right = mid + 1; // starting index of right half of arr

  // storing elements in the temporary array in a sorted manner
  while (left <= mid && right <= high) {
    if (arr[left] <= arr[right]) {
      temp.push(arr[left]);
      left++;
    } else {
      temp.push(arr[right]);
      right++;
    }
  }

  // if elements on the left half are still left
  while (left <= mid) {
    temp.push(arr[left]);
    left++;
  }

  // if elements on the right half are still left
  while (right <= high) {
    temp.push(arr[right]);
    right++;
  }

  // transferring all elements from temporary to arr
  for (let i = low; i <= high; i++) {
    arr[i] = temp[i - low];
  }
}

function countPairs(arr, low, mid, high) {
  let right = mid + 1;
  let cnt = 0;
  for (let i = low; i <= mid; i++) {
    while (right <= high && arr[i] > 2 * arr[right]) right++;
    cnt += right - (mid + 1);
  }
  return cnt;
}

function mergeSort(arr, low, high) {
  let cnt = 0;
  if (low >= high) return cnt;
  let mid = Math.floor((low + high) / 2);
  cnt += mergeSort(arr, low, mid); // left half
  cnt += mergeSort(arr, mid + 1, high); // right half
  cnt += countPairs(arr, low, mid, high); // Modification
  merge(arr, low, mid, high); // merging sorted halves
  return cnt;
}

function team(skill, n) {
  return mergeSort(skill, 0, n - 1);
}

let a = [4, 1, 2, 3, 1];
let n = 5;
let cnt = team(a, n);
console.log("The number of reverse pair is: " + cnt);

```

**Time Complexity:** O(2N*logN), where N = size of the given array.

**Space Complexity:** O(N), as in the merge sort We use a temporary array to store elements in sorted order.

