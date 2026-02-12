# Merge Two Sorted Lists - LeetCode Solution

This repository contains a JavaScript solution for the [LeetCode Problem: Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/).

---

## Problem Statement

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one **sorted list**. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.


### Constraints

- The number of nodes in both lists is in the range `[0, 50]`.
- `-100 <= Node.val <= 100`
- Both `list1` and `list2` are sorted in **non-decreasing order**.

---

## Solution

We solve this problem using a **dummy node approach** to simplify merging two sorted linked lists.

- Traverse both lists at the same time.
- At each step, attach the smaller node to the merged list.
- Move forward in the list from which the node was taken.
- After finishing one list, attach the remaining nodes of the other list.

This approach ensures **O(n + m)** time complexity and **O(1)** extra space (besides the output list).

---

## JavaScript Implementation

```javascript
// Definition for singly-linked list.
function ListNode(val, next) {
    this.val = (val===undefined ? 0 : val)
    this.next = (next===undefined ? null : next)
}

/**
 * Merge two sorted linked lists.
 * @param {ListNode} list1
 * @param {ListNode} list2
 * @return {ListNode}
 */
var mergeTwoLists = function(list1, list2) {
    let dummy = new ListNode(-1);
    let current = dummy;

    while (list1 !== null && list2 !== null) {
        if (list1.val <= list2.val) {
            current.next = list1;
            list1 = list1.next;
        } else {
            current.next = list2;
            list2 = list2.next;
        }
        current = current.next;
    }

    // Attach remaining nodes
    current.next = list1 !== null ? list1 : list2;

    return dummy.next;
};

