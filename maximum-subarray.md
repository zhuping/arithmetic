# 最大子序和（简单）

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

### 示例：

```
输入: [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```

### 进阶：

如果你已经实现复杂度为 O(n) 的解法，尝试使用更为精妙的分治法求解。

### 个人答案

动态规划思路，假设索引值为 `n` 的最大和为 dp[n]，那么 dp[n] = max(dp[n - 1] + nums[n], nums[n])

```js
var maxSubArray = function(nums) {
  let dp = [], max = -Infinity;
  dp[0] = nums[0];
  for (let i = 1; i < nums.length; i++) {
    dp[i] = Math.max(dp[i - 1] + nums[i], nums[i]);
  }

  dp.forEach(v => {
    max = v > max ? v : max;
  })

  return max;
};
```

### 好的思路

空间复杂度降到 O(1)

```js
var maxSubArray = function(nums) {
  let pre = nums[0], maxAns = nums[0];
  for (let i = 1; i < nums.length; i++) {
    pre = Math.max(pre + nums[i], nums[i]);
    maxAns = Math.max(maxAns, pre);
  }
  return maxAns;
}
```

* [题目地址](https://leetcode-cn.com/problems/maximum-subarray/)