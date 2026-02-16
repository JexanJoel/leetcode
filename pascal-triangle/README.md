# 118. Pascal's Triangle

## 🧠 Problem

Given an integer `numRows`, return the first `numRows` of Pascal's triangle.

In Pascal's triangle:
- The first and last element of each row is `1`
- Every other element is the sum of the two numbers directly above it

### Example

Input:
```
numRows = 5
```

Output:
```
[
  [1],
  [1,1],
  [1,2,1],
  [1,3,3,1],
  [1,4,6,4,1]
]
```

---

## 🚀 Approach

We build the triangle **row by row** using a bottom-up approach.

### Key Observations:
- Row `i` has `i + 1` elements
- First and last elements are always `1`
- Middle elements follow:

```
triangle[i][j] = triangle[i-1][j-1] + triangle[i-1][j]
```

This is a **Dynamic Programming** pattern because each row depends on the previous row.

---

## 💻 JavaScript Solution

```javascript
var generate = function(numRows) {
    const result = [];

    for (let i = 0; i < numRows; i++) {
        // Create a row filled with 1s
        const row = new Array(i + 1).fill(1);

        // Update middle elements
        for (let j = 1; j < i; j++) {
            row[j] = result[i - 1][j - 1] + result[i - 1][j];
        }

        result.push(row);
    }

    return result;
};
```

---

## ⏱ Time & Space Complexity

- **Time Complexity:** O(n²)  
- **Space Complexity:** O(n²)

Since `1 <= numRows <= 30`, this solution is efficient.

---

## 🧩 Why This Works

- We start with an empty result array.
- For each row:
  - Initialize with all 1’s.
  - Fill middle values using the previous row.
  - Push the row into the result.
- Return the completed triangle.

---

## 📌 Concepts Used

- Dynamic Programming (Bottom-Up)
- Nested Loops
- Array Manipulation

---

## ✅ Edge Case

If `numRows = 1`, output will be:

```
[[1]]
```

---

Happy Coding 🚀
