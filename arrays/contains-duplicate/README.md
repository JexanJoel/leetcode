# Contains Duplicate (LeetCode – Easy)

## 🧩 Problem Statement

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is **distinct**.

---

## 🛠️ Approach Used

**Algorithm:** Hashing using a **Set**  
**Why Set?**
- A `Set` stores only **unique values**
- It provides **O(1)** average time lookup
- Perfect for checking if we have seen a value before

---

## 💡 Idea

- Traverse the array once
- Keep track of elements already seen using a `Set`
- If an element already exists in the set → duplicate found
- Otherwise, add it to the set
- If loop finishes → no duplicates

---

## ✅ JavaScript Solution

```js
var containsDuplicate = function(nums) {
    let seen = new Set();

    for (let i = 0; i < nums.length; i++) {
        if (seen.has(nums[i])) {
            return true;
        }
        seen.add(nums[i]);
    }

    return false;
};
