# 盛最多水的容器（中等）

给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0) 。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

说明：你不能倾斜容器。

### 示例 1：

![](https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg)

```
输入：[1,8,6,2,5,4,8,3,7]
输出：49 
解释：图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。
```

### 示例2：

```
输入：height = [1,1]
输出：1
```

### 示例3：

```
输入：height = [4,3,2,1,4]
输出：16
```

### 示例4：

```
输入：height = [1,2,1]
输出：2
```

### 提示：

* n = height.length
* 2 <= n <= 3 * 104
* 0 <= height[i] <= 3 * 104

### 个人答案

通过双指针的方式，为了盛水最大，每次移动较小的那个高度

```js
var maxArea = function(height) {
  let start = 0, end = height.length - 1;
  let max = 0;

  while(start < end) {
    let area = Math.min(height[start], height[end]) * (end - start);
    max = Math.max(area, max);

    if (height[start] < height[end]) {
      start++;
    } else {
      end--;
    }
  }

  return max;
};
```

* [题目地址](https://leetcode-cn.com/problems/container-with-most-water/)

