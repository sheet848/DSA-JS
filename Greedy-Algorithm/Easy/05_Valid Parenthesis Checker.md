To check if a string containing parentheses is valid, the **greedy algorithm** involves using a **stack** to track the opening brackets. Each closing bracket must correspond to the most recent unmatched opening bracket. Here’s an efficient implementation in JavaScript:

### **Valid Parenthesis Checker (Greedy Approach with Stack)**

```javascript
function isValidParenthesis(s) {
    const stack = [];
    const map = {
        ')': '(',
        '}': '{',
        ']': '['
    };

    for (let char of s) {
        if (char === '(' || char === '{' || char === '[') {
            // Push opening brackets onto the stack
            stack.push(char);
        } else {
            // For closing brackets, check if the stack's top matches
            if (stack.length === 0 || stack.pop() !== map[char]) {
                return false;
            }
        }
    }

    // If the stack is empty, all brackets were matched
    return stack.length === 0;
}

// Example usage:
const input1 = "()";
const input2 = "({[()]})";
const input3 = "({[}])";

console.log(isValidParenthesis(input1)); // true
console.log(isValidParenthesis(input2)); // true
console.log(isValidParenthesis(input3)); // false
```

---

### **Explanation**:

1. **Stack for Matching**:
    - Opening brackets (`(`, `{`, `[`) are pushed onto the stack.
    - When a closing bracket (`)`, `}`, `]`) is encountered, the stack is checked for its matching opening bracket (the most recent one).
2. **Mapping Brackets**:
    - A mapping object (`map`) is used to pair closing brackets with their respective opening brackets.
3. **Validation**:
    - If a closing bracket doesn’t match the stack’s top or the stack is empty when it’s needed, the string is invalid.
    - At the end, if the stack isn’t empty, unmatched brackets remain, so the string is invalid.
4. **Time Complexity**: **O(n)**, where `n` is the length of the string (each character is processed once).
5. **Space Complexity**: **O(n)**, for the stack in the worst case (e.g., all opening brackets like `"(((("`).

---

### Examples:

- **Input**: `"()"` → **Output**: `true` (valid parenthesis)
- **Input**: `"({[]})"` → **Output**: `true` (valid and nested correctly)
- **Input**: `"({[}])"` → **Output**: `false` (mismatch found)

This algorithm efficiently determines if parentheses are properly matched, making it optimal for such problems. Let me know if you'd like more explanations or variations!