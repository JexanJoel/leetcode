# 🔄 Move Zeroes (LeetCode 283)

## Problem
Given an integer array `nums`, move all `0`s to the end of the array while maintaining the relative order of the non-zero elements.

You must do this **in-place** without making a copy of the array.

---

## Approach
Use a pointer to track where the next non-zero element should be placed.

1. Traverse the array.
2. Whenever a non-zero element is found, place it at the current pointer position.
3. After placing all non-zero elements, fill the remaining positions with `0`.

This ensures order is preserved and no extra space is used.

---

## Algorithm Used
- Two Pointer Technique
- In-place Array Manipulation

---

## JavaScript Solution
```js
var moveZeroes = function(nums) {
    let index = 0;

    for (let i = 0; i < nums.length; i++) {
        if (nums[i] !== 0) {
            nums[index] = nums[i];
            index++;
        }
    }

    while (index < nums.length) {
        nums[index] = 0;
        index++;
    }
};
```

---

## Complexity
- Time: `O(n)`
- Space: `O(1)`
