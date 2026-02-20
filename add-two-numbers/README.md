# Add Two Numbers

## 🧠 Problem Statement

You are given two non-empty linked lists representing two non-negative integers.  
The digits are stored in reverse order, and each of their nodes contains a single digit.  
Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

---

## 📌 Examples

### Example 1
Input:
l1 = [2,4,3]  
l2 = [5,6,4]

Output:
[7,0,8]

Explanation:
342 + 465 = 807

---

### Example 2
Input:
l1 = [0]  
l2 = [0]

Output:
[0]

---

### Example 3
Input:
l1 = [9,9,9,9,9,9,9]  
l2 = [9,9,9,9]

Output:
[8,9,9,9,0,0,0,1]

---

## 🔍 Key Observations

- The digits are stored in **reverse order**.
- We add numbers the same way we do manually:
  - Digit by digit
  - Maintain a carry
- If one list is shorter, treat missing digits as 0.
- Continue until both lists and carry are fully processed.

---

## 🚀 Approach

1. Create a **dummy node** to build the result list.
2. Initialize `carry = 0`.
3. Traverse both linked lists:
   - Get values (or 0 if null).
   - Compute `sum = val1 + val2 + carry`.
   - Update:
     - `digit = sum % 10`
     - `carry = Math.floor(sum / 10)`
4. Create a new node with `digit`.
5. Move pointers forward.
6. Return `dummy.next`.

---

## 💻 JavaScript Solution

```javascript
function ListNode(val, next = null) {
    this.val = val;
    this.next = next;
}

var addTwoNumbers = function(l1, l2) {
    let dummy = new ListNode(0);
    let current = dummy;
    let carry = 0;

    while (l1 !== null || l2 !== null || carry !== 0) {
        let val1 = l1 ? l1.val : 0;
        let val2 = l2 ? l2.val : 0;

        let sum = val1 + val2 + carry;

        carry = Math.floor(sum / 10);
        let digit = sum % 10;

        current.next = new ListNode(digit);
        current = current.next;

        if (l1) l1 = l1.next;
        if (l2) l2 = l2.next;
    }

    return dummy.next;
};
```

---

## ⏱ Complexity Analysis

- **Time Complexity:** O(max(n, m))  
  We traverse both lists once.

- **Space Complexity:** O(max(n, m))  
  A new linked list is created for the result.

---

## 🎯 Why Use a Dummy Node?

Using a dummy node:
- Avoids edge case checks for the first node
- Simplifies linking logic
- Makes the code cleaner

---

## 🏁 Conclusion

This problem tests:
- Linked list traversal
- Carry handling
- Simulation of manual addition

A great example of combining pointer manipulation with basic math logic.