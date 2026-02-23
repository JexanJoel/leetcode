# 47. Permutations II

## 🧩 Problem

Given a collection of numbers `nums`, that might contain duplicates, return all possible **unique permutations** in any order.

### Example 1
Input:
nums = [1,1,2]

Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]

### Example 2
Input:
nums = [1,2,3]

Output:
[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

---

## 🚀 Approach (Backtracking + Sorting)

### Key Idea

1. Sort the array first.
2. Use backtracking.
3. Use a `used` array to track visited elements.
4. Skip duplicates using this condition:

```
if (i > 0 && nums[i] === nums[i - 1] && !used[i - 1]) continue;
```

This prevents duplicate permutations.

---

## 🧠 Why Sorting Helps

Sorting ensures duplicate numbers are next to each other, making it easy to detect and skip repeated branches.

---

## 💻 JavaScript Solution

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permuteUnique = function(nums) {
    const result = [];
    const current = [];
    const used = new Array(nums.length).fill(false);

    // Step 1: Sort the array
    nums.sort((a, b) => a - b);

    function backtrack() {
        // Base case
        if (current.length === nums.length) {
            result.push([...current]);
            return;
        }

        for (let i = 0; i < nums.length; i++) {

            // Skip used elements
            if (used[i]) continue;

            // Skip duplicates
            if (i > 0 && nums[i] === nums[i - 1] && !used[i - 1]) continue;

            // Choose
            used[i] = true;
            current.push(nums[i]);

            // Explore
            backtrack();

            // Unchoose (backtrack)
            used[i] = false;
            current.pop();
        }
    }

    backtrack();
    return result;
};
```

---

## ⏱ Time Complexity

- O(n! × n)
- Maximum n = 8 (safe for backtracking)

---

## 📌 Key Takeaways

- Always sort when dealing with duplicates in permutation problems.
- Use a `used[]` array to track selections.
- The duplicate skip condition is critical.

---

Happy Coding 🚀