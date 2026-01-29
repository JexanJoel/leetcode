# Maximum Subarray (LeetCode – Easy)

## 🧩 Problem Statement

Given an integer array `nums`, find the **contiguous subarray** (containing at least one number) which has the **largest sum**, and return that sum.

---

## 🛠️ Approach Used

**Algorithm:** Kadane’s Algorithm  
**Type:** Dynamic Programming (Optimized)

This algorithm works in **one pass** and decides at each index whether to:
- Continue the existing subarray, or
- Start a new subarray from the current element

---

## 💡 Core Idea

At every index, we ask:

> “Is it better to start fresh from this number, or continue the previous subarray?”

We track:
- `currentSum` → sum of the current subarray
- `maxSum` → maximum sum found so far

---

## ✅ JavaScript Solution

```js
var maxSubArray = function(nums) {
   let currentSum = nums[0];
   let maxSum = nums[0];

   for (let i = 1; i < nums.length; i++) {
       currentSum = Math.max(nums[i], nums[i] + currentSum);
       maxSum = Math.max(maxSum, currentSum);
   }

   return maxSum;
};
