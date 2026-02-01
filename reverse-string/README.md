# 🔁 Reverse String (LeetCode – Easy)

## 🧩 Problem Statement

Write a function that reverses a string.

The input string is given as an array of characters `s`.
You must reverse the array **in-place** with `O(1)` extra memory.

---

## 💡 Approach Used

### 🔹 Built-in Array Method

Since the input is already an **array of characters**, JavaScript provides a built-in method:

- `reverse()` → reverses the array **in-place**

No extra variables.
No extra memory.
Just one line.

---

## 🧠 Algorithm / Concept

- Array manipulation
- In-place operation

---

## 🧑‍💻 JavaScript Solution

```js
var reverseString = function(s) {
    s.reverse();
};

