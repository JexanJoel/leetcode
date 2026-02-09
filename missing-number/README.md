# 🔢 Missing Number (LeetCode 268)

## Problem
Given an array `nums` containing `n` distinct numbers in the range `[0, n]`,  
return the one number that is missing from the array.

---

## Approach
The numbers should contain all values from `0` to `n`.

1. Calculate the expected sum of numbers from `0` to `n` using the formula:
   ```
   n * (n + 1) / 2
   ```
2. Calculate the actual sum of all elements in the array.
3. Subtract the actual sum from the expected sum.
4. The result is the missing number.

This approach avoids sorting and extra space.

---

## Algorithm Used
- Math
- Array Traversal

---

## JavaScript Solution
```js
var missingNumber = function(nums) {
    let n = nums.length;
    let expectedSum = (n * (n + 1)) / 2;
    let actualSum = 0;

    for (let i = 0; i < nums.length; i++) {
        actualSum += nums[i];
    }

    return expectedSum - actualSum;
};
```

---

## Complexity
- Time: `O(n)`
- Space: `O(1)`
