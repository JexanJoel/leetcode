# 62. Unique Paths

## 🧩 Problem Statement

There is a robot on an **m x n grid**.  
The robot starts at the **top-left corner** (`grid[0][0]`) and wants to reach the **bottom-right corner** (`grid[m - 1][n - 1]`).

The robot can **only move right or down**.

Return the number of possible **unique paths**.

---

## 📌 Examples

### Example 1
Input:
m = 3  
n = 7  

Output:
28

---

### Example 2
Input:
m = 3  
n = 2  

Output:
3

Paths:
1. Right → Down → Down  
2. Down → Down → Right  
3. Down → Right → Down  

---

## 🚀 Approach 1 — Combinatorics (Optimal)

### 🔎 Key Idea

To reach the bottom-right corner:

- You must move **(m - 1) times down**
- You must move **(n - 1) times right**

Total moves =  
```
(m - 1) + (n - 1) = m + n - 2
```

Now the problem becomes:

> In total moves, how many ways can we arrange the downs (or rights)?

This is a **combination formula**:

```
C(m + n - 2, m - 1)
```

or

```
C(m + n - 2, n - 1)
```

---

### ✅ JavaScript Solution (Efficient)

```js
var uniquePaths = function(m, n) {
    let totalMoves = m + n - 2;
    let r = Math.min(m - 1, n - 1); // choose smaller for efficiency
    
    let result = 1;
    
    for (let i = 1; i <= r; i++) {
        result = result * (totalMoves - r + i) / i;
    }
    
    return Math.round(result);
};
```

### ⏱ Time Complexity
O(min(m, n))

### 📦 Space Complexity
O(1)

✔ Best for interviews

---

## 🚀 Approach 2 — Dynamic Programming (2D Array)

### 🔎 Idea

Each cell can be reached from:

- Top cell
- Left cell

So:

```
dp[i][j] = dp[i-1][j] + dp[i][j-1]
```

---

### ✅ JavaScript Solution

```js
var uniquePaths = function(m, n) {
    let dp = Array(m).fill(0).map(() => Array(n).fill(1));
    
    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            dp[i][j] = dp[i-1][j] + dp[i][j-1];
        }
    }
    
    return dp[m-1][n-1];
};
```

### ⏱ Time Complexity
O(m × n)

### 📦 Space Complexity
O(m × n)

✔ Easier to understand

---

## 🚀 Approach 3 — Space Optimized DP (1D Array)

Instead of a 2D grid, we use a single array.

---

### ✅ JavaScript Solution

```js
var uniquePaths = function(m, n) {
    let dp = Array(n).fill(1);
    
    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            dp[j] += dp[j-1];
        }
    }
    
    return dp[n-1];
};
```

### ⏱ Time Complexity
O(m × n)

### 📦 Space Complexity
O(n)

✔ Clean and efficient

---

## 🏁 Summary

| Approach | Time | Space | Best Use |
|----------|------|--------|----------|
| Combinatorics | O(min(m,n)) | O(1) | Interviews |
| 2D DP | O(m×n) | O(m×n) | Beginners |
| 1D DP | O(m×n) | O(n) | Optimized DP |

---

## 🎯 Final Recommendation

For interviews → Use **Combinatorics**  
For understanding concept → Use **2D DP**

---

## 📎 Constraints

- 1 ≤ m, n ≤ 100
- Answer ≤ 2 × 10⁹

---

Happy Coding 🚀