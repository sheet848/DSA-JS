
## Optimal Approach - Using XOR

```

function getSingleElement(arr) {
    // XOR all the elements:
    let xorr = 0;
    for (let i = 0; i < arr.length; i++) {
        xorr = xorr ^ arr[i];
    }
    return xorr;
}

function main() {
    let arr = [4, 1, 2, 1, 2];
    let ans = getSingleElement(arr);
    console.log("The single element is:", ans);
}

main();

```

**Time Complexity:** O(N)
**Space Complexity:** O(1) as we are not using any extra space.
