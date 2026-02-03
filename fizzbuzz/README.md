# 🧪 Fizz Buzz (LeetCode – Easy)

## 🧩 Problem Statement

Given an integer `n`, return a string array answer (1-indexed) where:

- `"FizzBuzz"` if `i` is divisible by **3 and 5**
- `"Fizz"` if `i` is divisible by **3**
- `"Buzz"` if `i` is divisible by **5**
- `i` (as a string) if none of the above conditions are true

---

## 💡 Approach Used

### 🔹 Conditional Logic + Loop

- Loop from `1` to `n`
- Check divisibility using the modulo operator `%`
- Push the correct value into the result array

---

## 🧠 Algorithm

1. Create an empty array `result`
2. Loop from `1` to `n` (inclusive)
3. For each number:
   - If divisible by both `3` and `5` → `"FizzBuzz"`
   - Else if divisible by `3` → `"Fizz"`
   - Else if divisible by `5` → `"Buzz"`
   - Else → convert number to string
4. Return the result array

---

## 🧑‍💻 JavaScript Solution

```js
var fizzBuzz = function(n) {
    let result = [];

    for (let i = 1; i <= n; i++) {
        if (i % 3 === 0 && i % 5 === 0) {
            result.push("FizzBuzz");
        } else if (i % 3 === 0) {
            result.push("Fizz");
        } else if (i % 5 === 0) {
            result.push("Buzz");
        } else {
            result.push(i.toString());
        }
    }

    return result;
};