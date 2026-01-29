# Valid Parentheses (LeetCode – Easy)

## 🧩 Problem Statement

Given a string `s` containing only the characters:

'(', ')', '{', '}', '[', ']'


Determine if the input string is **valid**.

A string is valid if:
- Open brackets are closed by the **same type** of brackets
- Open brackets are closed in the **correct order**
- Every closing bracket has a corresponding opening bracket

---

## 🛠️ Algorithm Used

### **Stack (LIFO – Last In, First Out)**

**Why Stack?**
- We need to keep track of the **most recent opening bracket**
- Closing brackets must match the **last unmatched opening bracket**

A stack is perfect for this behavior.

---

## 💡 Approach

1. Create an empty stack
2. Traverse the string character by character
3. Push opening brackets onto the stack
4. When a closing bracket is found:
   - If the stack is empty → invalid
   - Pop the top element and check if it matches
5. At the end, the stack must be empty for the string to be valid

---

## ✅ JavaScript Solution

```js
var isValid = function(s) {
    let stack = [];
    let map = {
        ')': '(',
        ']': '[',
        '}': '{'
    };

    for (let char of s) {
        if (char === '(' || char === '[' || char === '{') {
            stack.push(char);
        } else {
            if (stack.length === 0) return false;

            let top = stack.pop();
            if (top !== map[char]) return false;
        }
    }

    return stack.length === 0;
};
