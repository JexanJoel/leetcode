# 🔢 Power of Two (LeetCode – Easy)

## 🧩 Problem Statement

Given an integer `n`, return `true` if it is a **power of two**.  
Otherwise, return `false`.

A number is a power of two if it can be written as `2^x` where `x` is an integer.

---

## 💡 Approach Used

### 🔹 Repeated Division (Beginner Friendly)

- Powers of two are **positive numbers**
- They can be **repeatedly divided by 2**
- If we eventually reach `1`, it is a power of two

---

## 🧠 Algorithm

1. If `n` is less than or equal to `0`, return `false`
2. While `n` is divisible by `2`:
   - Divide `n` by `2`
3. If the final value of `n` is `1`, return `true`
4. Otherwise, return `false`

---

## 🧑‍💻 JavaScript Solution

```js
var isPowerOfTwo = function(n) {
    if (n <= 0) return false;

    while (n % 2 === 0) {
        n = n / 2;
    }

    return n === 1;
};