# 5. Longest Palindromic Substring

## 🧩 Problem

Given a string `s`, return the **longest palindromic substring** in `s`.

A palindrome is a string that reads the same forward and backward.

---

## 📌 Examples

### Example 1

Input:
```
s = "babad"
```

Output:
```
"bab"
```

Explanation: `"aba"` is also a valid answer.

---

### Example 2

Input:
```
s = "cbbd"
```

Output:
```
"bb"
```

---

## 🔒 Constraints

- `1 <= s.length <= 1000`
- `s` consists only of digits and English letters.

---

# 🚀 Approach: Expand Around Center

Instead of generating all substrings (which would take O(n³) time), we use an optimized approach called **Expand Around Center**.

### Key Idea

Every palindrome expands from its center.

There are two types of palindromes:

1. Odd length → `"aba"` (center is a character)
2. Even length → `"abba"` (center is between two characters)

So for every index in the string, we:
- Expand around `(i, i)` → odd length
- Expand around `(i, i+1)` → even length
- Track the longest palindrome found

---

## ⏱ Complexity Analysis

- **Time Complexity:** O(n²)  
- **Space Complexity:** O(1)

---

# 💻 JavaScript Solution

```javascript
var longestPalindrome = function(s) {
    if (s.length < 2) return s;

    let start = 0;
    let maxLength = 0;

    const expandFromCenter = (left, right) => {
        while (left >= 0 && right < s.length && s[left] === s[right]) {
            left--;
            right++;
        }
        return right - left - 1;
    };

    for (let i = 0; i < s.length; i++) {
        let len1 = expandFromCenter(i, i);       // Odd length
        let len2 = expandFromCenter(i, i + 1);   // Even length
        let maxLen = Math.max(len1, len2);

        if (maxLen > maxLength) {
            maxLength = maxLen;
            start = i - Math.floor((maxLen - 1) / 2);
        }
    }

    return s.substring(start, start + maxLength);
};
```

---

# 🧠 How It Works (Step-by-Step)

### 1️⃣ Edge Case
If string length is less than 2, return it immediately since it is already a palindrome.

### 2️⃣ Expand From Center
The helper function:
- Expands outward while characters match
- Stops when mismatch happens
- Returns the length of the palindrome

### 3️⃣ Try Every Center
For each character:
- Check odd-length palindrome
- Check even-length palindrome
- Update longest substring if needed

### 4️⃣ Return Final Answer
Extract substring using:
```
s.substring(start, start + maxLength)
```

---

# 🔍 Example Walkthrough

Input:
```
"babad"
```

Checking centers:

- i = 0 → "b"
- i = 1 → "bab"
- i = 2 → "aba"
- i = 3 → "a"
- i = 4 → "d"

Longest palindrome found:
```
"bab"
```
(or `"aba"` — both are valid)

---

# ❌ Why Not Brute Force?

Brute force approach:
- Generate all substrings
- Check each one for palindrome
- Time Complexity: O(n³)

Expand Around Center:
- Cleaner logic
- Faster
- Constant space
- Interview friendly

---

# 🏁 Conclusion

This problem helps strengthen:
- Two pointer technique
- String manipulation
- Edge case handling
- Algorithm optimization

A must-know classic for coding interviews 🚀

---

⭐ If you found this helpful, consider starring the repository!

Happy Coding!