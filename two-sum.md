# 两数之和（简单题）

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

### 示例：

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

### 个人答案

思路：通过目标值去逐一减去数组中的元素，如果差值能在数组中，就返回两个数的下标

```js
var towSum = function(nums, target) {
  let pos = []
  for (let i = 0; i < nums.length; i++) {
    let value = nums[i]
    let endPos = nums.indexOf(target - value)
    if (endPos > -1 && endPos !== i) {
      pos = [i, endPos].concat(pos)
      break
    }
  }
}
```

* [题目地址](https://leetcode-cn.com/problems/two-sum/)

