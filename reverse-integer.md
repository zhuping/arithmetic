# 整数反转（简单题）

给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

### 示例1：

```
输入: 123
输出: 321
```

### 示例2：

```
输入: -123
输出: -321
```

### 示例3：

```
输入: 120
输出: 21
```

### 注意：

假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−231,  231 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。

### 个人答案

思路：先不管正负，通过绝对值全部变成整数，然后转成字符串，通过字符串的 `reverse` 做一次反转，然后再转回 Number 类型

```js
var reverse = function(x) {
  let rawX = x
  rawX = Math.abs(rawX).toString().solit('').reverse().join('')
  rawX = parseInt(rawX)

  if (x > 0) {
    return rawX >= Math.power(2, 31) ? 0 : rawX
  } else {
    return rawX >= Math.power(2, 31) ? 0 : -rawX
  }
}
```

### 好的思路

根据数学方法推导，‘弹出’和‘推入’计算

```js
//pop operation:
pop = x % 10;
x /= 10;

//push operation:
temp = rev * 10 + pop;
rev = temp;
```

* [题目地址](https://leetcode-cn.com/problems/reverse-integer/)