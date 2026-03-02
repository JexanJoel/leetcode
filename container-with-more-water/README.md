# 📦 Container With Most Water – LeetCode #11

## 🧠 Problem Statement

Given an integer array `height` of length `n`, there are `n` vertical lines drawn such that the two endpoints of the ith line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container that holds the **maximum amount of water**.

Return the maximum amount of water a container can store.

---

## 🧪 Example

### Input
```
height = [1,8,6,2,5,4,8,3,7]
```

### Output
```
49
```

### Explanation
The container formed between height `8` (index 1) and height `7` (index 8) gives:

```
Width = 8 - 1 = 7
Height = min(8, 7) = 7
Area = 7 × 7 = 49
```

---

## 🚀 Approach – Two Pointer Technique (Optimized)

### 🔹 Key Idea
- Start with two pointers:
  - `left` at the beginning
  - `right` at the end
- Calculate area using:
  
  ```
  width × min(height[left], height[right])
  ```
- Move the pointer with the **smaller height** inward.
- Keep updating the maximum area found.

### 🔹 Why Move the Smaller Height?
Because the water level is limited by the shorter line.  
Moving the taller line won't increase area if the shorter one remains limiting.

---

## 💻 JavaScript Solution

```javascript
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    let left = 0;
    let right = height.length - 1;
    let maxWater = 0;

    while (left < right) {
        let width = right - left;
        let minHeight = Math.min(height[left], height[right]);
        let area = width * minHeight;

        maxWater = Math.max(maxWater, area);

        // Move pointer of smaller height
        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }

    return maxWater;
};
```

---

## ⏱ Time & Space Complexity

| Complexity | Value |
|------------|--------|
| Time       | O(n)   |
| Space      | O(1)   |

- We traverse the array once → **Linear time**
- No extra data structures used → **Constant space**

---

## 🆚 Brute Force Approach (For Understanding)

### Idea:
Check every possible pair and compute the area.

### Time Complexity:
```
O(n²)
```

Not efficient for large inputs.

---

## 🎯 Key Takeaways

- Two pointer pattern is powerful for array problems.
- Always analyze how to reduce nested loops to linear scans.
- Think about what limits the answer (in this case, the shorter height).

---

## 📌 Tags

`Array` `Two Pointers` `Greedy`

---

## 👨‍💻 Author

Solving daily problems to improve problem-solving skills 🚀  
Feel free to connect and explore more solutions!
