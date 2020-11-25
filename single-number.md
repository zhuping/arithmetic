# 只出现一次的数字（简单题）

给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

### 说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

### 示例1：

```
输入: [2,2,1]
输出: 1
```

### 示例2：

```
输入: [4,1,2,1,2]
输出: 4
```

### 个人答案

思路：通过集合的方式，如果没有出现过，就放进集合，如果有出现过，就从集合中删除，这样剩下的就是目标元素

```js
var singleNumber = function(nums) {
  let target = [];
  for (let i = 0; i < nums.length; i++) {
    let currentNum = nums[i];
    let pos = target.indexOf(currentNum);
    if (pos === -1) {
      target.push(currentNum);
    } else {
      target.splice(pos, 1);
    }
  }
  return target[0];
};
```

### 好的思路

通过位运算

* 任何数和 00 做异或运算，结果仍然是原来的数，即 a⊕0=a。
* 任何数和其自身做异或运算，结果是 00，即 a⊕a=0。
* 异或运算满足交换律和结合律，即 a⊕b⊕a=b⊕a⊕a=b⊕(a⊕a)=b⊕0=b。

假设数组中有 `2m+1` 个数，其中有 `m` 个数各出现两次，一个数出现一次。令 a1、a2、... am 为出现两次的 `m` 个数，`am+1` 为出现一次的数。根据性质 3，数组中的全部元素的异或运算结果总是可以写成如下形式：

```js
var singleNumber = function(nums) {
  let single = 0;
  for (let i = 0; i < nums.length; i++) {
    let num = nums[i];
    single ^= num;
  }
  return single;
};
```
* [题目地址](https://leetcode-cn.com/problems/single-number/)