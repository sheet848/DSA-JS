```Javascript
function removeOuterParentheses(s) {
    let result = "";
    let depth = 0;

    for (let char of s) {
        if (char === '(') {
            if (depth > 0) { // Add '(' only if it's not an outer parenthesis
                result += char;
            }
            depth++;
        } else if (char === ')') {
            depth--;
            if (depth > 0) { // Add ')' only if it's not an outer parenthesis
                result += char;
            }
        }
    }

    return result;
}

// Example Usage
let s = "(()())(())";
console.log(removeOuterParentheses(s)); // Output: "()()()"

```

### Explanation:

1. The `depth` variable keeps track of the current nesting level of parentheses.
    
2. When encountering `'('`, it's added to the `result` only if it's not the outermost parenthesis (`depth > 0`), and then the depth increases.
    
3. Similarly, when encountering `')'`, it's added only if `depth > 0` before decreasing the depth.
    

This JavaScript solution is efficient, with a time complexity of **O(n)** where `n` is the length of the string. Let me know if you'd like further details or a different approach!