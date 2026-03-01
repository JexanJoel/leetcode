# 88. Merge Sorted Array

## 🟢 Difficulty: Easy  
🔗 LeetCode Problem 88

---

## 📘 Problem Statement

You are given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

Merge `nums1` and `nums2` into a single array sorted in non-decreasing order.

The final sorted array should **not be returned**, but instead be stored inside the array `nums1`.

To accommodate this:
- `nums1` has a length of `m + n`
- The first `m` elements are valid
- The last `n` elements are `0` and should be ignored
- `nums2` has length `n`

---

## 🧠 Approach (Optimal O(m + n) Solution)

Since `nums1` already has extra space at the end, we merge from **back to front**.

### 🔹 Why from the back?
If we merge from the front, we risk overwriting values in `nums1` that we haven't processed yet.

### 🔹 Three Pointer Strategy
- `i = m - 1` → Last valid element in `nums1`
- `j = n - 1` → Last element in `nums2`
- `k = m + n - 1` → Last index of `nums1`

Compare elements from the end and place the larger one at position `k`.

---

## 💻 JavaScript Solution

```javascript
var merge = function(nums1, m, nums2, n) {
    let i = m - 1;       // pointer for nums1
    let j = n - 1;       // pointer for nums2
    let k = m + n - 1;   // pointer for placement

    // Merge while both arrays have elements
    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[k] = nums1[i];
            i--;
        } else {
            nums1[k] = nums2[j];
            j--;
        }
        k--;
    }

    // If nums2 still has elements left
    while (j >= 0) {
        nums1[k] = nums2[j];
        j--;
        k--;
    }
};
```

---

## 🔍 Example

### Example 1

Input:
```
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6], n = 3
```

Output:
```
[1,2,2,3,5,6]
```

---

### Example 2

Input:
```
nums1 = [1], m = 1
nums2 = [], n = 0
```

Output:
```
[1]
```

---

### Example 3

Input:
```
nums1 = [0], m = 0
nums2 = [1], n = 1
```

Output:
```
[1]
```

---

## ⏱️ Complexity Analysis

- **Time Complexity:** O(m + n)  
- **Space Complexity:** O(1) (in-place)

---

## 🎯 Key Takeaways

- Always consider filling from the back when extra space is available.
- Avoid unnecessary shifting.
- Two-pointer technique is extremely powerful for sorted arrays.
- In-place merging saves memory.

---

## 🚀 Summary

This solution efficiently merges two sorted arrays in linear time without using extra space by leveraging the empty slots at the end of `nums1`.

Perfect example of:
- Two pointers
- In-place array manipulation
- Greedy comparison strategy

---

Happy Coding 💻🔥