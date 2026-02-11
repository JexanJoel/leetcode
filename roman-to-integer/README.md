# LeetCode 13: Roman to Integer (Easy)

Convert a Roman numeral to an integer.  

## Problem Statement

Roman numerals are represented by seven symbols:

| Symbol | Value |
|--------|-------|
| I      | 1     |
| V      | 5     |
| X      | 10    |
| L      | 50    |
| C      | 100   |
| D      | 500   |
| M      | 1000  |

- Roman numerals are usually written largest to smallest from left to right.  
- Subtraction rule:
  - I before V or X → 4 or 9
  - X before L or C → 40 or 90
  - C before D or M → 400 or 900  

Given a string `s` representing a Roman numeral, convert it to an integer.

## JavaScript Solution

```javascript

function romanToInt(s) {
    const romanMap = {
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000
    };

    let total = 0;

    for (let i = 0; i < s.length; i++) {
        const current = romanMap[s[i]];
        const next = romanMap[s[i + 1]];

        if (next && current < next) {
            total -= current; // subtraction case
        } else {
            total += current; // normal addition
        }
    }

    return total;
}


