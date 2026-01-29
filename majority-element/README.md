# Majority Element (LeetCode – Easy)

## 🧩 Problem Statement

Given an array `nums` of size `n`, return the **majority element**.

The majority element is the element that appears **more than ⌊n / 2⌋ times**.  
You may assume that the majority element **always exists** in the array.

---

## 🛠️ Algorithm Used

### ⭐ Boyer–Moore Voting Algorithm

- **Type:** Greedy Algorithm
- **Key Idea:** Pair and cancel out different elements
- **Optimal Solution**

---

## 💡 Intuition

The majority element appears **more than all other elements combined**.

So if we:
- Increase a counter when we see the same element
- Decrease it when we see a different element

All non-majority elements will cancel each other out,  
and the majority element will remain as the final candidate.

---

## ✅ JavaScript Solution (Optimal)

```js
var majorityElement = function(nums) {
    let candidate = null;
    let count = 0;

    for (let num of nums) {
        if (count === 0) {
            candidate = num;
        }

        if (num === candidate) {
            count++;
        } else {
            count--;
        }
    }

    return candidate;
};
