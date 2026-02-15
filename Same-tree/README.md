# Same Tree

## 🧠 Problem

Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not.

Two binary trees are considered the same if:
- They are structurally identical.
- The nodes have the same value.

---

## 📌 Examples

### Example 1
```
Input:  p = [1,2,3], q = [1,2,3]
Output: true
```

### Example 2
```
Input:  p = [1,2], q = [1,null,2]
Output: false
```

### Example 3
```
Input:  p = [1,2,1], q = [1,1,2]
Output: false
```

---

## 📎 Constraints

- Number of nodes in both trees: `[0, 100]`
- `-10^4 <= Node.val <= 10^4`

---

## 💡 Approach (Recursive)

Binary trees are naturally recursive.

To check if two trees are the same:

1. If both nodes are `null` → return `true`
2. If one is `null` → return `false`
3. If values are different → return `false`
4. Recursively compare:
   - Left subtree
   - Right subtree

Both left and right must match.

---

## 🚀 JavaScript Solution

```javascript
var isSameTree = function(p, q) {
    // If both nodes are null, they match
    if (p === null && q === null) {
        return true;
    }

    // If one is null and the other is not, structure differs
    if (p === null || q === null) {
        return false;
    }

    // If values are different, trees are not the same
    if (p.val !== q.val) {
        return false;
    }

    // Recursively compare left and right subtrees
    return isSameTree(p.left, q.left) && 
           isSameTree(p.right, q.right);
};
```

---

## 🔍 Dry Run Example

For:

```
p = [1,2,3]
q = [1,2,3]
```

Comparison flow:

```
Compare 1 === 1
  Compare 2 === 2
  Compare 3 === 3
All matched → true
```

---

## ⏱ Time Complexity

```
O(n)
```

We visit each node once.

---

## 💾 Space Complexity

```
O(h)
```

- `h` = height of tree (recursion stack)
- Worst case (skewed tree): `O(n)`
- Balanced tree: `O(log n)`

---

## 🏁 Key Takeaway

A binary tree can be defined recursively:

```
Tree = Root + Left Subtree + Right Subtree
```

So to check if two trees are identical:

```
Root must match
Left subtree must match
Right subtree must match
```

If all three conditions are satisfied → trees are the same.
