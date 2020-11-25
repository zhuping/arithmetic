# 爬楼梯（简单题）

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

### 示例1：

```
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
```

### 示例2：

```
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
```

### 个人答案

动态规划思路：要考虑第爬到第 n 阶楼梯时候可能是一步，也可能是两步：
1.计算爬上 n-1 阶楼梯的方法数量，因为再爬 1 阶就到第 n 阶
2.计算爬上 n-2 阶楼梯体方法数量，因为再爬 2 阶就到第 n 阶 那么 dp[n] = dp[n-1] + dp[n-2]

为什么不是 dp[n] = dp[n-1] + 1 + dp[n-2] + 2 呢，因为 dp[n] 是爬楼梯方法数量，不是爬到 n 阶楼梯的步数

```js
var climbStairs = function(n) {
  if (n <= 1) return n;

  let dp = new Array(n);
  dp[0] = 0;
  dp[1] = 1;
  dp[2] = 2;

  for (let i = 3; i <= n; i++) {
    dp[i] = dp[i - 1] + dp[i - 2];
  }

  return dp[n];
};
```

### 好的思路

通过观察发现，只有两个状态在更新下一次状态的时候，才会被使用，如果只记录这两个状态，可以把空间复杂度降到 O(1)

```js
var climbStairs = function(n) {
  if (n <= 1) return n;

  let first = 1;
  let second = 2;

  for (let i = 3; i <= n; i++) {
    let third = first + second;
    first = second;
    second = third;
  }

  return second;
};
```

* [题目地址](https://leetcode-cn.com/problems/climbing-stairs/)