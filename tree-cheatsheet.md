| #  | Question                                                                                                                                    | Core Concept              | Must Know Keywords            |
| -- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- | ----------------------------- |
| 1  | [Inorder Traversal (Iterative & Recursive)](https://leetcode.com/problems/binary-tree-inorder-traversal/)                                   | DFS, Stack                | Left → Root → Right           |
| 2  | [Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)                                                         | DFS, Stack                | Root → Left → Right           |
| 3  | [Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)                                                       | DFS, Stack                | Left → Right → Root           |
| 4  | [Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)                                                   | BFS, Queue                | Level-wise                    |
| 5  | [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)                                                           | DFS, Height               | Max(left + right)             |
| 6  | [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)                                                 | DFS                       | Base case + 1                 |
| 7  | [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)                                                                 | DFS with pruning          | abs(left - right) ≤ 1         |
| 8  | [Same Tree](https://leetcode.com/problems/same-tree/)                                                                                       | DFS, Recursion            | Compare node values           |
| 9  | [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)                                                                             | Mirror check              | Compare left & right subtrees |
| 10 | [Path Sum](https://leetcode.com/problems/path-sum/)                                                                                         | DFS + subtraction         | root-to-leaf with sum         |
| 11 | [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)                           | DFS, recursion            | Return when you find p or q   |
| 12 | [Construct Binary Tree from Inorder and Preorder](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) | Recursion + Hashmap       | Divide at root index          |
| 13 | [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)                                                   | DFS + range validation    | min < val < max               |
| 14 | [Kth Smallest Element in BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)                                                 | Inorder Traversal         | BST → Sorted Inorder          |
| 15 | [Convert Sorted Array to BST](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)                                    | Divide and Conquer        | Middle element as root        |
| 16 | [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)                               | BFS or DFS                | Encode structure              |
| 17 | [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)                                                   | BFS + level-wise tracking | Right-most node               |
| 18 | [Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)                                     | Postorder, reverse pre    | Modify pointers               |
| 19 | [Populating Next Right Pointers](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)                                | BFS + pointers            | Use queue or O(1) connect     |
| 20 | [Vertical Order Traversal of Binary Tree](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)                         | BFS + coordinates         | Group by column index         |


=============================================================================================================================================================================

# 🧠 Tree Data Structures - Google L5 Prep Cheatsheet

This guide includes **20 must-practice Tree questions** commonly asked in L5 interviews at top tech companies like Google. Each entry includes the **concept**, **keywords**, and **solution code** with explanations in Python.

---

## 📌 Traversals

### 1. Inorder Traversal (Iterative & Recursive)

**Concept:** DFS using Stack
**Keywords:** Left → Root → Right
🔗 [https://leetcode.com/problems/binary-tree-inorder-traversal/](https://leetcode.com/problems/binary-tree-inorder-traversal/)

```python
# Recursive
def inorderTraversal(root):
    return inorderTraversal(root.left) + [root.val] + inorderTraversal(root.right) if root else []

# Iterative
def inorderTraversal(root):
    res, stack = [], []
    while root or stack:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        res.append(root.val)
        root = root.right
    return res
```

### 2. Preorder Traversal

**Concept:** DFS
**Keywords:** Root → Left → Right
🔗 [https://leetcode.com/problems/binary-tree-preorder-traversal/](https://leetcode.com/problems/binary-tree-preorder-traversal/)

```python
def preorderTraversal(root):
    if not root: return []
    stack, output = [root], []
    while stack:
        node = stack.pop()
        output.append(node.val)
        if node.right: stack.append(node.right)
        if node.left: stack.append(node.left)
    return output
```

### 3. Postorder Traversal

**Concept:** DFS
**Keywords:** Left → Right → Root
🔗 [https://leetcode.com/problems/binary-tree-postorder-traversal/](https://leetcode.com/problems/binary-tree-postorder-traversal/)

```python
def postorderTraversal(root):
    if not root: return []
    stack, output = [root], []
    while stack:
        node = stack.pop()
        output.append(node.val)
        if node.left: stack.append(node.left)
        if node.right: stack.append(node.right)
    return output[::-1]
```

---

## 📏 Structural Questions

### 4. Level Order Traversal

**Concept:** BFS using Queue
🔗 [https://leetcode.com/problems/binary-tree-level-order-traversal/](https://leetcode.com/problems/binary-tree-level-order-traversal/)

```python
from collections import deque

def levelOrder(root):
    if not root: return []
    q, res = deque([root]), []
    while q:
        level = []
        for _ in range(len(q)):
            node = q.popleft()
            level.append(node.val)
            if node.left: q.append(node.left)
            if node.right: q.append(node.right)
        res.append(level)
    return res
```

### 5. Diameter of Binary Tree

**Concept:** DFS with height
🔗 [https://leetcode.com/problems/diameter-of-binary-tree/](https://leetcode.com/problems/diameter-of-binary-tree/)

```python
def diameterOfBinaryTree(root):
    diameter = 0
    def height(node):
        nonlocal diameter
        if not node: return 0
        l, r = height(node.left), height(node.right)
        diameter = max(diameter, l + r)
        return 1 + max(l, r)
    height(root)
    return diameter
```

### 6. Maximum Depth of Binary Tree

**Concept:** DFS
🔗 [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

```python
def maxDepth(root):
    if not root: return 0
    return 1 + max(maxDepth(root.left), maxDepth(root.right))
```

### 7. Balanced Binary Tree

**Concept:** DFS with pruning
🔗 [https://leetcode.com/problems/balanced-binary-tree/](https://leetcode.com/problems/balanced-binary-tree/)

```python
def isBalanced(root):
    def check(node):
        if not node: return 0
        l = check(node.left)
        if l == -1: return -1
        r = check(node.right)
        if r == -1 or abs(l - r) > 1: return -1
        return 1 + max(l, r)
    return check(root) != -1
```

---

## 🧙 Comparisons & Validations

### 8. Same Tree

**Concept:** DFS Recursion
🔗 [https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)

```python
def isSameTree(p, q):
    if not p and not q: return True
    if not p or not q or p.val != q.val: return False
    return isSameTree(p.left, q.left) and isSameTree(p.right, q.right)
```

### 9. Symmetric Tree

**Concept:** Mirror Check
🔗 [https://leetcode.com/problems/symmetric-tree/](https://leetcode.com/problems/symmetric-tree/)

```python
def isSymmetric(root):
    def isMirror(t1, t2):
        if not t1 and not t2: return True
        if not t1 or not t2 or t1.val != t2.val: return False
        return isMirror(t1.left, t2.right) and isMirror(t1.right, t2.left)
    return isMirror(root, root)
```

---

## 🧲 Math + Path Problems

### 10. Path Sum

**Concept:** DFS
🔗 [https://leetcode.com/problems/path-sum/](https://leetcode.com/problems/path-sum/)

```python
def hasPathSum(root, targetSum):
    if not root: return False
    if not root.left and not root.right:
        return targetSum == root.val
    return hasPathSum(root.left, targetSum - root.val) or hasPathSum(root.right, targetSum - root.val)
```

### 11. Lowest Common Ancestor

**Concept:** DFS
🔗 [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

```python
def lowestCommonAncestor(root, p, q):
    if not root or root == p or root == q: return root
    left = lowestCommonAncestor(root.left, p, q)
    right = lowestCommonAncestor(root.right, p, q)
    return root if left and right else left or right
```

---

## 💡 Tree Construction & Validation

### 12. Construct Binary Tree from Inorder and Preorder

**Concept:** Recursion + HashMap
🔗 [https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

```python
def buildTree(preorder, inorder):
    idx_map = {val: idx for idx, val in enumerate(inorder)}
    def helper(p_left, p_right, i_left, i_right):
        if p_left > p_right: return None
        root_val = preorder[p_left]
        root = TreeNode(root_val)
        index = idx_map[root_val]
        left_size = index - i_left
        root.left = helper(p_left + 1, p_left + left_size, i_left, index - 1)
        root.right = helper(p_left + left_size + 1, p_right, index + 1, i_right)
        return root
    return helper(0, len(preorder) - 1, 0, len(inorder) - 1)
```

### 13. Validate Binary Search Tree

**Concept:** DFS + Range
🔗 [https://leetcode.com/problems/validate-binary-search-tree/](https://leetcode.com/problems/validate-binary-search-tree/)

```python
def isValidBST(root):
    def validate(node, low=-float('inf'), high=float('inf')):
        if not node: return True
        if node.val <= low or node.val >= high: return False
        return validate(node.left, low, node.val) and validate(node.right, node.val, high)
    return validate(root)
```

### 14. Kth Smallest in BST

**Concept:** Inorder Traversal
🔗 [https://leetcode.com/problems/kth-smallest-element-in-a-bst/](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

```python
def kthSmallest(root, k):
    stack = []
    while True:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        k -= 1
        if k == 0:
            return root.val
        root = root.right
```

### 15. Convert Sorted Array to BST

**Concept:** Divide & Conquer
🔗 [https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

```python
def sortedArrayToBST(nums):
    if not nums: return None
    mid = len(nums) // 2
    root = TreeNode(nums[mid])
    root.left = sortedArrayToBST(nums[:mid])
    root.right = sortedArrayToBST(nums[mid + 1:])
    return root
```

---

## 🔄 Serialization & Views

### 16. Serialize and Deserialize Binary Tree

**Concept:** DFS or BFS
🔗 [https://leetcode.com/problems/serialize-and-deserialize-binary-tree/](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)

```python
class Codec:
    def serialize(self, root):
        if not root: return "X"
        return f'{root.val},{self.serialize(root.left)},{self.serialize(root.right)}'

    def deserialize(self, data):
        def dfs(nodes):
            val = next(nodes)
            if val == 'X': return None
            node = TreeNode(int(val))
            node.left = dfs(nodes)
            node.right = dfs(nodes)
            return node
        return dfs(iter(data.split(',')))
```

### 17. Right Side View

**Concept:** BFS
🔗 [https://leetcode.com/problems/binary-tree-right-side-view/](https://leetcode.com/problems/binary-tree-right-side-view/)

```python
from collections import deque

def rightSideView(root):
    if not root: return []
    q, view = deque([root]), []
    while q:
        size = len(q)
        for i in range(size):
            node = q.popleft()
            if i == size - 1:
                view.append(node.val)
            if node.left: q.append(node.left)
            if node.right: q.append(node.right)
    return view
```

### 18. Flatten Binary Tree to Linked List

**Concept:** Postorder traversal
🔗 [https://leetcode.com/problems/flatten-binary-tree-to-linked-list/](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)

```python
def flatten(root):
    if not root: return
    flatten(root.left)
    flatten(root.right)
    if root.left:
        temp = root.right
        root.right = root.left
        root.left = None
        while root.right:
            root = root.right
        root.right = temp
```

### 19. Populating Next Right Pointers

**Concept:** BFS with Queue or O(1)
🔗 [https://leetcode.com/problems/populating-next-right-pointers-in-each-node/](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

```python
def connect(root):
    if not root: return None
    level = root
    while level.left:
        curr = level
        while curr:
            curr.left.next = curr.right
            if curr.next:
                curr.right.next = curr.next.left
            curr = curr.next
        level = level.left
    return root
```

### 20. Vertical Order Traversal

**Concept:** BFS + column index
🔗 [https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)

```python
from collections import defaultdict, deque

def verticalTraversal(root):
    nodes = defaultdict(list)
    q = deque([(root, 0, 0)])
    while q:
        node, x, y = q.popleft()
        nodes[x].append((y, node.val))
        if node.left:
            q.append((node.left, x - 1, y + 1))
        if node.right:
            q.append((node.right, x + 1, y + 1))
    res = []
    for x in sorted(nodes):
        col = [val for y, val in sorted(nodes[x])]
        res.append(col)
    return res
```

---

> Tip: Master these patterns and solve variations to crack any tree-based interview round!

