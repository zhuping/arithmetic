# 两数相加（中等）

给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

### 示例：

```
输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807
```

### 个人答案

由于理解错成数组了，用了数组的方式来处理，以数组较长的链表做循环，较短的链表不足补0

```js
var addTwoNumbers = function(l1, l2) {
  let len = Math.max(l1.length, l2.length);
  let target = [];

  let i = 0, plus = 0, remain = 0;
  while (i < len) {
    let a = l1[i] !== undefined ? l1[i] : 0;
    let b = l2[i] !== undefined ? l2[i] : 0;
    let result = a + b + plus;
    plus = parseInt(result / 10);
    remain = result % 10;
    target.push(remain);
    i++;
  }

  return target;
};
```

### 官方答案

```js
var addTwoNumbers = function(l1, l2) {
  let head = null, tail = null;
  let carry = 0;
  while(l1 || l2) {
    const n1 = l1 ? l1.val : 0;
    const n2 = l2 ? l2.val : 0;
    const sum = n1 + n2 + carry;

    if (!head) {
      head = tail = new ListNode(sum % 10);
    } else {
      tail.next = new ListNode(sum % 10);
      tail = tail.next;
    }
    carry = Math.floor(sum / 10);
    if (l1) {
      l1 = l1.next;
    }
    if (l2) {
      l2 = l2.next;
    }
  }
  if (carry > 0) {
    tail.next = new ListNode(carry);
  }
  return head;
};
```

* [题目地址](https://leetcode-cn.com/problems/add-two-numbers/)