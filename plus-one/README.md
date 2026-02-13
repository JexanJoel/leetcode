# ➕ Plus One – JavaScript Solution

This project solves the classic **“Plus One”** problem.

You are given a large integer represented as an array of digits. Each element in the array represents a single digit, ordered from most significant to least significant.

Your task is to increment the integer by one and return the resulting array of digits.

---

## 📌 Problem Statement

Given:

```
digits = [1,2,3]
```

The array represents the integer:

```
123
```

After incrementing by one:

```
123 + 1 = 124
```

Return:

```
[1,2,4]
```

---

## ✅ Examples

### Example 1

**Input**
```
[1,2,3]
```

**Output**
```
[1,2,4]
```

---

### Example 2

**Input**
```
[4,3,2,1]
```

**Output**
```
[4,3,2,2]
```

---

### Example 3

**Input**
```
[9]
```

**Output**
```
[1,0]
```

---

## 🚀 JavaScript Solution

```javascript
function plusOne(digits) {
    // Traverse from last digit
    for (let i = digits.length - 1; i >= 0; i--) {
        
        // If current digit is less than 9, increment and return
        if (digits[i] < 9) {
            digits[i]++;
            return digits;
        }

        // If digit is 9, set to 0 (carry over)
        digits[i] = 0;
    }

    // If all digits were 9, add 1 at the beginning
    digits.unshift(1);
    return digits;
}
```

---

## 🧠 How It Works

1. Start from the last digit.
2. If the digit is less than 9 → increment and return.
3. If the digit is 9 → set it to 0 and carry 1 to the next digit.
4. If all digits are 9 → add 1 at the beginning.

---

## ⏱ Time Complexity

- **O(n)** — In the worst case (e.g., `[9,9,9]`), we traverse the entire array.

## 💾 Space Complexity

- **O(1)** — We modify the array in place (except when adding a new leading digit).

---

## 📂 Usage

```javascript
console.log(plusOne([1,2,3])); // [1,2,4]
console.log(plusOne([9,9,9])); // [1,0,0,0]
```

---

## 📜 Constraints

- `1 <= digits.length <= 100`
- `0 <= digits[i] <= 9`
- No leading zeros in the input array

---

Feel free to fork, modify, and use this solution for learning or interview preparation 🚀
