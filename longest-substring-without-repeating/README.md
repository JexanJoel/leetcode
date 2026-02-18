# LeetCode #3 - Longest Substring Without Repeating Characters

## Problem Description

Given a string `s`, find the **length of the longest substring without repeating characters**.


---

## Approach / Algorithm

We use a **sliding window** technique combined with a **hash map** to track the last index of each character.

### Steps:

1. Initialize two pointers for the sliding window: `start` and `end`.  
2. Use a map to store the latest index of each character.  
3. Iterate through the string with `end`:
   - If the current character is **already in the map and inside the window**, move `start` to `map[char] + 1`.
   - Update the character's latest index in the map.
   - Update the `maxLen` with `end - start + 1`.  
4. Return `maxLen`.

This ensures we scan each character only once — **O(n) time**.

---

## JavaScript Solution

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let start = 0;               // sliding window start
    let maxLen = 0;              // maximum length
    const map = new Map();       // character -> latest index

    for (let end = 0; end < s.length; end++) {
        const char = s[end];

        // if character is repeated inside current window
        if (map.has(char) && map.get(char) >= start) {
            // move start just after previous occurrence
            start = map.get(char) + 1;
        }

        // record latest index of char
        map.set(char, end);

        // update max length
        maxLen = Math.max(maxLen, end - start + 1);
    }

    return maxLen;
};

---