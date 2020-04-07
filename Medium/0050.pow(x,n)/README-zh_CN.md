# 0050. Pow(x, n)

[English](./README.md) ｜ 简体中文



##  题目描述

实现 [pow(x, n)](https://www.cplusplus.com/reference/valarray/pow/) ，即计算 x 的 n 次幂函数。

**示例 1：**

>**输入：** 2.00000, 10
>**输出：** 1024.00000

**示例 2：**

>**输入：** 2.10000, 3
>**输出：** 9.26100

**示例 3：**

>**输入：** 2.00000, -2
>**输出：** 0.25000
>**解释：** 2^(-2) = 1 / (2^2) = 1/4 = 0.25

**说明：**

- -100.0 < *x* < 100.0
- *n* 是 32 位有符号整数，其数值范围是 [−2^31, 2^31 − 1] 。



## 题解

```swift
class Solution {
    func myPow(_ x: Double, _ n: Int) -> Double {
        if n == 0 {
            return 1
        }
        if n < 0 {
            return 1 / myPow(x, -n)
        }
        let m = myPow(x, n / 2)
        if n & 1 == 0 {
            return m * m
        }
        return m * m * x
    }
}
```

