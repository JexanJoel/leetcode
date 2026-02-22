# Letter Combinations of a Phone Number

Generate all possible letter combinations for a given phone number string (digits 2-9) based on the traditional telephone keypad mapping.

---

## Problem Description

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Digit `1` does not map to any letters.

### Constraints

- 1 <= digits.length <= 4  
- digits[i] is a digit in the range ['2', '9']

---

## Approach / Logic

1. **Digit-to-Letters Mapping:**  

| Digit | Letters |
|-------|---------|
| 2     | abc     |
| 3     | def     |
| 4     | ghi     |
| 5     | jkl     |
| 6     | mno     |
| 7     | pqrs    |
| 8     | tuv     |
| 9     | wxyz    |

2. **Backtracking Algorithm:**  
   - Use recursion to build all possible combinations.  
   - Start with an empty combination and index 0.  
   - At each step, append one letter from the current digit and move to the next digit.  
   - Once all digits are processed, save the combination.  

---

## JavaScript Implementation

```javascript
function letterCombinations(digits) {
    if (!digits || digits.length === 0) return [];

    const digitMap = {
        '2': 'abc',
        '3': 'def',
        '4': 'ghi',
        '5': 'jkl',
        '6': 'mno',
        '7': 'pqrs',
        '8': 'tuv',
        '9': 'wxyz'
    };

    const result = [];

    function backtrack(index, combination) {
        // Base case: combination complete
        if (index === digits.length) {
            result.push(combination);
            return;
        }

        // Get letters corresponding to current digit
        const letters = digitMap[digits[index]];
        for (let letter of letters) {
            // Append letter and move to next digit
            backtrack(index + 1, combination + letter);
        }
    }

    backtrack(0, ""); // Start recursion
    return result;
}

// Example usage
console.log(letterCombinations("23"));
// Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
