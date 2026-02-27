# 292. Nim Game

## 🧩 Problem Statement

You are playing the following Nim Game with your friend:

- There is a heap of stones.
- You go first.
- On each turn, a player removes **1 to 3 stones**.
- Whoever removes the last stone **wins**.
- Both players play optimally.

Given `n`, return `true` if you can win the game, otherwise return `false`.

---

## 💡 Key Insight

The losing positions are when `n` is a multiple of **4**.

### Why?

If there are 4 stones:

- If you remove 1 → opponent removes 3 (wins)
- If you remove 2 → opponent removes 2 (wins)
- If you remove 3 → opponent removes 1 (wins)

No matter what you do, opponent wins.

This pattern repeats for:
- 4
- 8
- 12
- 16
- ...

So:

```
If n % 4 === 0 → You Lose
If n % 4 !== 0 → You Win
```

---

## 🚀 JavaScript Solution

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var canWinNim = function(n) {
    return n % 4 !== 0;
};
```

---

## ⏱ Complexity Analysis

- **Time Complexity:** O(1)
- **Space Complexity:** O(1)

---

## 🧠 Pattern Summary

Winning positions:
1, 2, 3, 5, 6, 7, 9, 10, 11, ...

Losing positions:
4, 8, 12, 16, ...

All multiples of 4 are losing states.

---

## 🔥 Final Takeaway

This is a mathematical pattern recognition problem — not a simulation or DP problem.

Just remember:

```
return n % 4 !== 0;
```

---

Happy Coding 🚀