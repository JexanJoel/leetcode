# 👑 N-Queens Problem

## 🔗 Problem Link
N-Queens – Hard  
Platform: LeetCode

---

## 🧠 Problem Statement

The n-queens puzzle is the problem of placing **n queens** on an **n × n chessboard** such that no two queens attack each other.

A queen can attack:
- Same column
- Same row
- Same diagonal (both directions)

Given an integer `n`, return **all distinct solutions** to the n-queens puzzle.

Each solution should be represented as a board of strings:
- `'Q'` → Queen
- `'.'` → Empty space

---

## 📌 Example 1

Input:
```
n = 4
```

Output:
```
[
 [".Q..",
  "...Q",
  "Q...",
  "..Q."],

 ["..Q.",
  "Q...",
  "...Q",
  ".Q.."]
]
```

There are **2 distinct solutions** for n = 4.

---

## 📌 Example 2

Input:
```
n = 1
```

Output:
```
[["Q"]]
```

---

# 🚀 Approach

We solve this using **Backtracking**.

### 🔥 Strategy

We place queens **row by row**.

At each row:
1. Try every column
2. Check if placing a queen is SAFE
3. If safe → place it
4. Move to next row
5. If stuck → backtrack (remove queen)

---

## ⚡ Optimization

Instead of checking the whole board every time, we track:

- `cols` → occupied columns
- `diag1` → main diagonals (row - col)
- `diag2` → anti-diagonals (row + col)

This allows:
- Safety check in **O(1)** time
- Efficient pruning

---

# 🧩 Algorithm

1. Initialize empty board
2. Use recursion starting from row = 0
3. For each column:
   - If column or diagonal is used → skip
   - Else:
     - Place queen
     - Mark column & diagonals
     - Recurse for next row
     - Remove queen (backtrack)
4. When row == n → store solution

---

# 💻 JavaScript Solution

```javascript
var solveNQueens = function(n) {
    const result = [];
    const board = Array.from({ length: n }, () => Array(n).fill('.'));

    const cols = new Set();
    const diag1 = new Set(); // row - col
    const diag2 = new Set(); // row + col

    function backtrack(row) {
        if (row === n) {
            result.push(board.map(r => r.join('')));
            return;
        }

        for (let col = 0; col < n; col++) {
            if (
                cols.has(col) ||
                diag1.has(row - col) ||
                diag2.has(row + col)
            ) {
                continue;
            }

            // Place queen
            board[row][col] = 'Q';
            cols.add(col);
            diag1.add(row - col);
            diag2.add(row + col);

            backtrack(row + 1);

            // Backtrack
            board[row][col] = '.';
            cols.delete(col);
            diag1.delete(row - col);
            diag2.delete(row + col);
        }
    }

    backtrack(0);
    return result;
};
```

---

# ⏱ Complexity Analysis

### Time Complexity
```
O(N!)
```
In worst case, we try many permutations of queen placements.

### Space Complexity
```
O(N)
```
- Recursion stack
- Sets for columns and diagonals

---

# 🧠 Key Concepts Used

- Backtracking
- Recursion
- Set data structure
- Pruning search space

---

# 🎯 Why This Works

Instead of brute-forcing every board:
- We eliminate invalid placements early
- We only explore safe configurations
- That’s why this is efficient for n ≤ 9

---

# 🏆 Final Thoughts

N-Queens is a classic recursion + backtracking problem.

Mastering this problem improves:
- Recursive thinking
- State tracking
- Constraint-based search problems

---

⭐ If you found this helpful, consider starring the repository!
