# 101.对称二叉树（简单）

给定一个二叉树，检查它是否是镜像对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

```
    1
   / \
  2   2
   \   \
   3    3
```

### 个人答案

通过 DFS 栈的方式

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function(root) {
  let stack = []
  stack.push([ root.left, root.right ])

  while(stack.length) {
    let [ leftNode, rightNode ] = stack.pop()
    if (leftNode === null && rightNode === null) {
      continue
    }

    if (leftNode === null || rightNode === null) {
      return false
    }

    if (leftNode.val !== rightNode.val) {
      return false
    }

    stack.push([ leftNode.left, rightNode.right ], [ leftNode.right, rightNode.left ])
  }
  return true
};
```

* [题目地址](https://leetcode-cn.com/problems/symmetric-tree/)