# 📏 Length of Last Word (LeetCode – Easy)

## 🧩 Problem Statement

Given a string `s` consisting of words and spaces, return the **length of the last word** in the string.

A **word** is defined as a maximal substring consisting of non-space characters only.

---


## 💡 Approach Used

### 🔹 String Manipulation

1. **Trim** the string to remove leading and trailing spaces.
2. **Split** the string into an array of words using space `" "`.
3. Access the **last word** from the array.
4. Return the **length** of that word.

---

## 🧠 Algorithm / Concept

- String manipulation
- Arrays
- Indexing

---

## 🧑‍💻 JavaScript Solution

```js
var lengthOfLastWord = function(s) {
    let words = s.trim().split(" ");
    return words[words.length - 1].length;
};