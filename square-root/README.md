# 69. Sqrt(x)

## Problem
Given a non-negative integer `x`, return the square root of `x` rounded down to the nearest integer.

Built-in exponent functions are not allowed.

---

## Approach
This problem is solved using **Binary Search**.

Instead of checking every number, we search between `1` and `x` and repeatedly:
- Pick the middle value
- Compare `mid * mid` with `x`
- Adjust the search range

The last value whose square is less than or equal to `x` is the answer.

---

## Algorithm Used
Binary Search

---

## Time Complexity
O(log x)

---

## Space Complexity
O(1)

---

## JavaScript Solution
```javascript
var mySqrt = function(x) {
    if (x < 2) return x;

    let left = 1;
    let right = x;
    let answer = 0;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (mid * mid === x) {
            return mid;
        }

        if (mid * mid < x) {
            answer = mid;
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return answer;
};
