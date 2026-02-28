# 202. Happy Number

## 🟢 Easy

### 📝 Problem Statement

Write an algorithm to determine if a number `n` is a **happy number**.

A happy number is defined by the following process:

1. Starting with any positive integer.
2. Replace the number with the **sum of the squares of its digits**.
3. Repeat the process until:
   - The number equals `1` → (it will stay at 1), OR
   - It loops endlessly in a cycle that does **not** include `1`.

Return `true` if `n` is a happy number, otherwise return `false`.

---

### 📌 Example 1

```
Input: n = 19
Output: true
Explanation:
1² + 9² = 82
8² + 2² = 68
6² + 8² = 100
1² + 0² + 0² = 1
```

### 📌 Example 2

```
Input: n = 2
Output: false
```

---

## 🚀 Approach 1: Using Set (Cycle Detection)

### 💡 Idea
- Keep calculating the sum of squares.
- Store visited numbers in a `Set`.
- If we reach `1` → return `true`.
- If a number repeats → cycle detected → return `false`.

### 💻 JavaScript Solution

```javascript
var isHappy = function(n) {
    const seen = new Set();
    
    while (n !== 1 && !seen.has(n)) {
        seen.add(n);
        n = getSumOfSquares(n);
    }
    
    return n === 1;
};

function getSumOfSquares(num) {
    let sum = 0;
    
    while (num > 0) {
        let digit = num % 10;
        sum += digit * digit;
        num = Math.floor(num / 10);
    }
    
    return sum;
}
```

### ⏱ Complexity
- **Time Complexity:** O(log n)
- **Space Complexity:** O(log n)

---

## ⚡ Approach 2: Floyd’s Cycle Detection (O(1) Space)

### 💡 Idea
Use two pointers:
- `slow` → moves one step
- `fast` → moves two steps

If they meet (not at 1), it's a cycle.

### 💻 JavaScript Solution

```javascript
var isHappy = function(n) {
    let slow = n;
    let fast = getSumOfSquares(n);

    while (fast !== 1 && slow !== fast) {
        slow = getSumOfSquares(slow);
        fast = getSumOfSquares(getSumOfSquares(fast));
    }

    return fast === 1;
};

function getSumOfSquares(num) {
    let sum = 0;
    
    while (num > 0) {
        let digit = num % 10;
        sum += digit * digit;
        num = Math.floor(num / 10);
    }
    
    return sum;
}
```

### ⏱ Complexity
- **Time Complexity:** O(log n)
- **Space Complexity:** O(1)

---

## 🧠 Key Takeaways

- Happy numbers eventually reach `1`.
- All non-happy numbers fall into a repeating cycle.
- Can be solved using:
  - HashSet (easier to understand)
  - Floyd’s Cycle Detection (optimal space)

---

⭐ Clean implementation + optimal solution ready for interviews!