The "Isomorphic Strings" problem is about determining whether two strings can be mapped to each other character by character in a consistent one-to-one manner. Here's how you can solve this in JavaScript:

```Javascript

function isIsomorphic(s, t) {
    if (s.length !== t.length) return false; // Strings of different lengths can't be isomorphic

    let mapST = {};
    let mapTS = {};

    for (let i = 0; i < s.length; i++) {
        const charS = s[i];
        const charT = t[i];

        // Check mapping from s to t
        if (mapST[charS] === undefined) {
            mapST[charS] = charT;
        } else if (mapST[charS] !== charT) {
            return false;
        }

        // Check mapping from t to s
        if (mapTS[charT] === undefined) {
            mapTS[charT] = charS;
        } else if (mapTS[charT] !== charS) {
            return false;
        }
    }

    return true;
}

// Example Usage
let s = "egg";
let t = "add";
console.log(isIsomorphic(s, t)); // Output: true

s = "foo";
t = "bar";
console.log(isIsomorphic(s, t)); // Output: false

s = "paper";
t = "title";
console.log(isIsomorphic(s, t)); // Output: true

```

### Explanation:

1. **Mapping Character Relationships**:
    
    - Two maps (`mapST` and `mapTS`) are used to track one-to-one mappings between characters in `s` and `t` and ensure they are consistent in both directions.
        
2. **Iteration**:
    
    - Iterate through each character of both strings simultaneously.
        
    - If the current characters don't match the established mapping, return `false`.
        
3. **Consistency**:
    
    - If the mappings remain consistent for all characters, return `true`.
        

### Key Points:

- The function ensures that each character in `s` maps to only one character in `t` and vice versa.
    
- The time complexity is **O(n)**, where `n` is the length of the strings.
    

Let me know if you'd like further explanation or additional examples!