# Search Insert Position

## 🧩 Problem

Given a sorted array of distinct integers and a target value, return the index if the target is found.

If not, return the index where it would be inserted in order.

You must write an algorithm with **O(log n)** runtime complexity.

---

## 💡 Approach (Binary Search)

Since the array is sorted and we need O(log n) time complexity, we use **Binary Search**.

Binary Search works by:
1. Finding the middle element.
2. Comparing it with the target.
3. If target is smaller → search the left half.
4. If target is larger → search the right half.
5. If not found → the position where `left` stops is the correct insert index.

At the end of the loop:
- If the target exists → return its index.
- If not → `left` will be the correct insertion position.

---

## 🚀 JavaScript Solution

```javascript
function searchInsert(nums, target) {
    let left = 0;
    let right = nums.length - 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (nums[mid] === target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return left;
}
```

---

## 🔍 Example Walkthrough

### Example 1
Input:
```
nums = [1,3,5,6], target = 5
```
Output:
```
2
```

---

### Example 2
Input:
```
nums = [1,3,5,6], target = 2
```
Output:
```
1
```

---

### Example 3
Input:
```
nums = [1,3,5,6], target = 7
```
Output:
```
4
```

---

## ⏱ Complexity Analysis

- **Time Complexity:** O(log n)  
  (Binary search halves the search space each iteration)

- **Space Complexity:** O(1)  
  (No extra space used)

---

## 📌 Key Takeaway

Binary Search is the go-to approach when:
- The array is sorted
- You need O(log n) performance
- You need to find a value or its correct position

---
