# 199.二叉树的右视图（中等）

给定一棵二叉树，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。

### 示例

```
输入: [1,2,3,null,5,null,4]
输出: [1, 3, 4]
解释:

   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---
```

### 个人答案

通过 BFS 队列的方式遍历，i === len -1 代表遍历到当前行的最右侧了

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
 * @return {number[]}
 */
var rightSideView = function(root) {
  let queue = [], node = []
  queue.push(root)

  while (queue.length) {
    let len = queue.length
    for (let i = 0; i < len; i++) {
      let item = queue.shift()

      if (!item) continue
      if (i === len - 1) node.push(item.val)

      if (item.left) queue.push(item.left) 
      if (item.right) queue.push(item.right) 
    }
  }

  return node
};
```

* [题目地址](https://leetcode-cn.com/problems/binary-tree-right-side-view/)