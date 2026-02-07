# LeetCode 9 – Palindrome Number

## 🧩 Problem
Given an integer `x`, return `true` if `x` is a palindrome, and `false` otherwise.

A palindrome number reads the same forward and backward.

### Examples
- `121` → true  
- `-121` → false  
- `10` → false  

---

## 💡 Approach (Simple & Easy)

We use a **string-based approach** for clarity.

### Logic
1. Negative numbers can never be palindromes → return `false`
2. Convert the number to a string
3. Reverse the string
4. Compare the original string with the reversed string
5. If both are equal → palindrome

---

## ✅ JavaScript Solution

```js
var isPalindrome = function(x) {
    if (x < 0) return false;

    let str = x.toString();
    let reversed = str.split('').reverse().join('');

    return str === reversed;
};
