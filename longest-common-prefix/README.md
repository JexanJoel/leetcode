# 🔤 Longest Common Prefix (LeetCode – Easy)

## 🧩 Problem Statement

Given an array of strings, return the **longest common prefix** among them.  
If there is no common prefix, return an empty string `""`.

---

## 💡 Approach Used

### 🔹 Horizontal Scanning

- Assume the first string is the prefix
- Compare it with each subsequent string
- Reduce the prefix until it matches the beginning of every string
- Stop when the prefix becomes empty or fully matches

---

## 🧠 Algorithm

1. If the input array is empty, return an empty string
2. Initialize the prefix as the first string
3. Loop through the remaining strings
4. While the current string does not start with the prefix:
   - Remove the last character from the prefix
   - If the prefix becomes empty, return an empty string
5. Return the final prefix

---

## 🧑‍💻 JavaScript Solution

```js
var longestCommonPrefix = function(strs) {
    if (strs.length === 0) {
        return "";
    }

    let prefix = strs[0];

    for (let i = 1; i < strs.length; i++) {
        while (strs[i].indexOf(prefix) !== 0) {
            prefix = prefix.slice(0, prefix.length - 1);
            if (prefix === "") return "";
        }
    }

    return prefix;
};
