# 18. 4Sum – JavaScript Solution

## 🧩 Problem Statement

Given an array `nums` of `n` integers, return all unique quadruplets  
`[nums[a], nums[b], nums[c], nums[d]]` such that:

- `0 <= a, b, c, d < n`
- `a, b, c, d` are distinct
- `nums[a] + nums[b] + nums[c] + nums[d] == target`

You may return the answer in any order.

---

## 📌 Examples

### Example 1
Input:
nums = [1,0,-1,0,-2,2]  
target = 0  

Output:
[[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]

---

### Example 2
Input:
nums = [2,2,2,2,2]  
target = 8  

Output:
[[2,2,2,2]]

---

# 💡 Approach

This is an extension of the 3Sum problem.

Instead of checking all combinations (O(n⁴)), we optimize using:

1. Sort the array
2. Fix first number (i loop)
3. Fix second number (j loop)
4. Use two pointers (left & right) for remaining two numbers
5. Skip duplicates carefully

Time Complexity: O(n³)  
Space Complexity: O(1) (excluding output)

---

# 🧠 Algorithm Steps

1. Sort the array.
2. Loop through array with index `i`.
3. Inside that, loop with index `j`.
4. Use:
   - left = j + 1
   - right = n - 1
5. Calculate sum of four numbers.
6. If:
   - sum == target → push to result
   - sum < target → move left++
   - sum > target → move right--
7. Skip duplicates at every level.

---

# ✅ JavaScript Implementation

```javascript
var fourSum = function(nums, target) {
    const result = [];
    const n = nums.length;

    // Step 1: Sort the array
    nums.sort((a, b) => a - b);

    for (let i = 0; i < n - 3; i++) {

        // Skip duplicate values for i
        if (i > 0 && nums[i] === nums[i - 1]) continue;

        for (let j = i + 1; j < n - 2; j++) {

            // Skip duplicate values for j
            if (j > i + 1 && nums[j] === nums[j - 1]) continue;

            let left = j + 1;
            let right = n - 1;

            while (left < right) {
                const sum = nums[i] + nums[j] + nums[left] + nums[right];

                if (sum === target) {
                    result.push([nums[i], nums[j], nums[left], nums[right]]);

                    // Skip duplicates for left
                    while (left < right && nums[left] === nums[left + 1]) left++;

                    // Skip duplicates for right
                    while (left < right && nums[right] === nums[right - 1]) right--;

                    left++;
                    right--;
                } 
                else if (sum < target) {
                    left++;
                } 
                else {
                    right--;
                }
            }
        }
    }

    return result;
};
```

---

# 🔍 Why Duplicate Skipping Matters

Example:
nums = [2,2,2,2,2], target = 8

Without skipping duplicates, `[2,2,2,2]` would appear multiple times.

With proper duplicate handling:
✔ Only one unique quadruplet is returned.

---

# 🎯 Key Pattern to Remember

2Sum → HashMap  
3Sum → Sort + 1 loop + 2 pointers  
4Sum → Sort + 2 loops + 2 pointers  
kSum → Recursion

---

# 🚀 Final Notes

- Always sort first.
- Always skip duplicates.
- Think of 4Sum as a 3Sum inside a loop.
- This pattern is very common in coding interviews.

Happy Coding 🔥