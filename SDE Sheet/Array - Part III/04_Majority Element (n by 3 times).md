**Problem Statement:** Given an array of N integers. Find the elements that appear more than **N/3** times in the array. If no such element exists, return an empty vector.

**Example 1:****Input Format**: N = 5, array[] = {1,2,2,3,2}
**Result**: 2
**Explanation:** Here we can see that the Count(1) = 1, Count(2) = 3 and Count(3) = 1.Therefore, the count of 2 is greater than N/3 times. Hence, 2 is the answer.

**Example 2:****Input Format**:  N = 6, array[] = {11,33,33,11,33,11}
**Result:** 11 33
**Explanation:** Here we can see that the Count(11) = 3 and Count(33) = 3. Therefore, the count of both 11 and 33 is greater than N/3 times. Hence, 11 and 33 is the answer.

# Solution

### **Extended Boyer Moore’s Voting Algorithm)**:

```Javascript

function majorityElement(v) {
    let n = v.length; // size of the array

    let cnt1 = 0, cnt2 = 0; // counts
    let el1 = -Infinity; // element 1
    let el2 = -Infinity; // element 2

    // applying the Extended Boyer Moore's Voting Algorithm:
    for (let i = 0; i < n; i++) {
        if (cnt1 === 0 && el2 !== v[i]) {
            cnt1 = 1;
            el1 = v[i];
        }
        else if (cnt2 === 0 && el1 !== v[i]) {
            cnt2 = 1;
            el2 = v[i];
        }
        else if (v[i] === el1) cnt1++;
        else if (v[i] === el2) cnt2++;
        else {
            cnt1--, cnt2--;
        }
    }

    let ls = []; // list of answers

    // Manually check if the stored elements in
    // el1 and el2 are the majority elements:
    cnt1 = 0, cnt2 = 0;
    for (let i = 0; i < n; i++) {
        if (v[i] === el1) cnt1++;
        if (v[i] === el2) cnt2++;
    }

    let mini = Math.floor(n / 3) + 1;
    if (cnt1 >= mini) ls.push(el1);
    if (cnt2 >= mini) ls.push(el2);

    // Uncomment the following line
    // if it is told to sort the answer array:
    // ls.sort(); // TC --> O(2*log2) ~ O(1);

    return ls;
}

let arr = [11, 33, 33, 11, 33, 11];
let ans = majorityElement(arr);
console.log("The majority elements are: " + ans.join(" "));


```
**Time Complexity:** O(N) + O(N), where N = size of the given array.  
**Reason:** The first O(N) is to calculate the counts and find the expected majority elements. The second one is to check if the calculated elements are the majority ones or not.

**Space Complexity:** O(1) as we are only using a list that stores a maximum of 2 elements. The space used is so small that it can be considered constant.