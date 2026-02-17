# 168. Excel Sheet Column Title

## 🟢 Easy

### 🧩 Problem Statement

Given an integer `columnNumber`, return its corresponding column title as it appears in an Excel sheet.

For example:

```
A -> 1  
B -> 2  
C -> 3  
...  
Z -> 26  
AA -> 27  
AB -> 28  
...
```

---

### 📥 Examples

#### Example 1:
```
Input: columnNumber = 1
Output: "A"
```

#### Example 2:
```
Input: columnNumber = 28
Output: "AB"
```

#### Example 3:
```
Input: columnNumber = 701
Output: "ZY"
```

---

### 🔒 Constraints

```
1 <= columnNumber <= 2^31 - 1
```

---

## 🧠 Approach

This problem is similar to **base-26 conversion**, but with a twist:

- Excel columns are **1-based** (A = 1, not 0)
- There is **no zero character**
- Before using modulo (`% 26`), we must subtract 1

### Key Idea

1. Subtract 1 from `columnNumber`
2. Get remainder using `% 26`
3. Convert remainder to character using:
   ```js
   String.fromCharCode(65 + remainder)
   ```
4. Divide number by 26 using `Math.floor`
5. Repeat until `columnNumber` becomes 0

---

## 💻 JavaScript Solution

```js
/**
 * @param {number} columnNumber
 * @return {string}
 */
var convertToTitle = function(columnNumber) {
    let result = "";

    while (columnNumber > 0) {
        columnNumber--; // Adjust for 1-based indexing
        
        let remainder = columnNumber % 26;
        
        result = String.fromCharCode(65 + remainder) + result;
        
        columnNumber = Math.floor(columnNumber / 26);
    }

    return result;
};
```

---

## 🧪 Test Cases

```js
console.log(convertToTitle(1));   // "A"
console.log(convertToTitle(28));  // "AB"
console.log(convertToTitle(701)); // "ZY"
```

---

## ⏱️ Complexity Analysis

- **Time Complexity:** O(log₍26₎ n)  
- **Space Complexity:** O(log₍26₎ n)

---

## 🎯 Why `columnNumber--` Is Important

If we don’t subtract 1:

- `26 % 26 = 0`
- This would incorrectly map to a non-existent zero character
- Excel columns do not contain zero — they start from 1

That’s the key trick that makes this problem interesting 🚀

---

### 💡 Related Concept

This problem is essentially a modified **base conversion** problem with a custom alphabet mapping.

---

⭐ If this helped, consider starring the repo!
