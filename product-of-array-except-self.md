# 238.除自身以外数组的乘积（中等）

给你一个长度为 n 的整数数组 nums，其中 n > 1，返回输出数组 output ，其中 output[i] 等于 nums 中除 nums[i] 之外其余各元素的乘积。

### 示例

```
输入: [1,2,3,4]
输出: [24,12,8,6]
```

提示：题目数据保证数组之中任意元素的全部前缀元素和后缀（甚至是整个数组）的乘积都在 32 位整数范围内。

说明: 请不要使用除法，且在 O(n) 时间复杂度内完成此题。

### 个人答案

L[i] 记录位置为 `i` 的左侧乘积，R[i] 记录位置为 `i` 的右侧乘积，那么位置 `i` 的总乘积为 L[i] * R[i]

```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var productExceptSelf = function(nums) {
  let L = [], R = [], ans = []
  L[0] = 1, R[nums.length - 1] = 1 
  for (let i = 1; i < nums.length; i++) {
    L[i] = L[i - 1] * nums[i - 1]
  }

  for (let i = nums.length - 2; i >= 0; i--) {
    R[i] = R[i + 1] * nums[i + 1]
  }

  for (let i = 0; i < nums.length; i++) {
    ans[i] = L[i] * R[i]
  }
  return ans
};
```

* [题目地址](https://leetcode-cn.com/problems/product-of-array-except-self/)