```Javascript
function reverseWords(s) {
    // Split the string by spaces, filter out empty parts, and reverse the array
    return s.trim().split(/\s+/).reverse().join(" ");
}

// Example Usage
let input = "  Hello   World!  ";
console.log(reverseWords(input)); // Output: "World! Hello"

```

### Explanation:

1. `trim()`: Removes leading and trailing spaces from the string.
    
2. `split(/\s+/)`: Splits the string into an array of words, treating multiple spaces as a single separator.
    
3. `reverse()`: Reverses the order of the words in the array.
    
4. `join(" ")`: Combines the reversed array back into a single string with a single space between words.
    

This approach works efficiently with a time complexity of **O(n)** where `n` is the length of the string. Let me know if you'd like more details or a different solution!

## Without Build in

```Javascript
function reverseWordsWithoutBuiltIn(s) {
    let trimmed = "", result = "", word = "";
    let i = 0, length = s.length;

    // Trim leading spaces
    while (i < length && s[i] === " ") i++;
    
    // Traverse the string to remove extra spaces
    while (i < length) {
        if (s[i] === " " && trimmed[trimmed.length - 1] !== " ") {
            trimmed += " ";
        } else if (s[i] !== " ") {
            trimmed += s[i];
        }
        i++;
    }

    // Trim trailing space if present
    if (trimmed[trimmed.length - 1] === " ") {
        trimmed = trimmed.slice(0, trimmed.length - 1);
    }

    // Iterate from the end to reverse the words
    for (i = trimmed.length - 1; i >= 0; i--) {
        if (trimmed[i] === " ") {
            result += word + " ";
            word = "";
        } else {
            word = trimmed[i] + word;
        }
    }
    
    // Append the last word
    result += word;

    return result;
}

// Example Usage
let input = "  Hello   World!  ";
console.log(reverseWordsWithoutBuiltIn(input)); // Output: "World! Hello"

```