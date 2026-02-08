# 🪜 Min Cost Climbing Stairs (LeetCode 746)

## Problem
You are given an array `cost` where `cost[i]` is the cost of the `i`th step.
Once you pay the cost, you can either climb one or two steps.

You can start from step `0` or step `1`.

Return the minimum cost to reach the top.

---

## Approach
To reach step `i`, you must come from:
- step `i - 1`
- step `i - 2`

At each step, choose the minimum cost path.

This problem uses **Dynamic Programming (Bottom-Up)** and keeps track of only the last two results to optimize space.

---

## Algorithm Used
- Dynamic Programming

---

## JavaScript Solution
```js
var minCostClimbingStairs = function(cost) {
    let prev2 = 0;
    let prev1 = 0;

    for (let i = 2; i <= cost.length; i++) {
        let current = Math.min(
            prev1 + cost[i - 1],
            prev2 + cost[i - 2]
        );
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
