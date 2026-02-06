# 🪜 Climbing Stairs (LeetCode 70)

## Problem
You are climbing a staircase with `n` steps. Each time, you can climb either 1 step or 2 steps.

Return the total number of distinct ways to reach the top.

---

## Approach
To reach step `n`, you can come from:
- step `n - 1` (1 step)
- step `n - 2` (2 steps)

So the number of ways is:
```
ways(n) = ways(n - 1) + ways(n - 2)
```

This follows a Dynamic Programming pattern.

---

## Algorithm Used
- Dynamic Programming (Bottom-Up)

---

## JavaScript Solution
```js
var climbStairs = function(n) {
    if (n <= 2) return n;

    let prev1 = 2;
    let prev2 = 1;

    for (let i = 3; i <= n; i++) {
        let current = prev1 + prev2;
        prev2 = prev1;
        prev1 = current;
    }

    return prev1;
};
```

---

## Complexity
- Time: `O(n)`
- Space: `O(1)`
