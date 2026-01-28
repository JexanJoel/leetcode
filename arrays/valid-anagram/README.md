# Valid Anagram (LeetCode – Easy)

## 🧩 Problem Statement

Given two strings `s` and `t`, return `true` if `t` is an **anagram** of `s`, and `false` otherwise.

An anagram is formed by rearranging the letters of a word using **all original letters exactly once**.

---

## 🛠️ Algorithm Used

**Hashing / Frequency Counting**

**Data Structure:** Hash Map (JavaScript Object)

This approach counts how many times each character appears in the first string and compares it with the second string.

---

## 💡 Approach

1. If the lengths of both strings are different, they cannot be anagrams
2. Create a hash map to store character frequencies
3. Count characters in the first string
4. Decrease counts using the second string
5. If a character count goes below zero or doesn’t exist, return `false`
6. If all checks pass, return `true`

---

## ✅ JavaScript Solution

```js
var isAnagram = function(s, t) {
    if (s.length !== t.length) return false;

    let count = {};

    for (let char of s) {
        count[char] = (count[char] || 0) + 1;
    }

    for (let char of t) {
        if (!count[char]) return false;
        count[char]--;
    }

    return true;
};
