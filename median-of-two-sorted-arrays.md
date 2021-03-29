# 4.寻找两个正序数组的中位数（困难）

给定两个大小分别为 m 和 n 的正序（从小到大）数组 nums1 和 nums2。请你找出并返回这两个正序数组的 中位数 。

### 示例 1：

```
输入：nums1 = [1,3], nums2 = [2]
输出：2.00000
解释：合并数组 = [1,2,3] ，中位数 2
```

### 示例 2：

```
输入：nums1 = [1,2], nums2 = [3,4]
输出：2.50000
解释：合并数组 = [1,2,3,4] ，中位数 (2 + 3) / 2 = 2.5
```

### 示例 3：

```
输入：nums1 = [0,0], nums2 = [0,0]
输出：0.00000
```

### 示例 4：

```
输入：nums1 = [], nums2 = [1]
输出：1.00000
```

### 示例 5：

```
输入：nums1 = [2], nums2 = []
输出：2.00000
```

### 个人答案

则当N为奇数时，![](https://bkimg.cdn.bcebos.com/formula/369410329320c73428e6e00bfda20122.svg)；当N为偶数时，![](https://bkimg.cdn.bcebos.com/formula/f0f3f443e3bc3e7a8bacf371ae430bda.svg)。

```
var findMedianSortedArrays = function(nums1, nums2) {
  let nums = nums1.concat(nums2)
  nums.sort((a, b) => a -b)

  let midNum
  let len = nums.length

  if (len % 2 === 1) {
    midNum = nums[((len + 1) / 2) - 1]
  } else {
    midNum = (nums[(len / 2) - 1] + nums[(len / 2)]) / 2
  }

  return midNum.toFixed(5)
};
```

* [题目地址](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)