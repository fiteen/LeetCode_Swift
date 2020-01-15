# 0029. 两数相除

[English](./README.md) ｜ 简体中文



##  题目描述

给定两个整数，被除数 `dividend` 和除数 `divisor`。将两数相除，要求不使用乘法、除法和 mod 运算符。

返回被除数 `dividend` 除以除数 `divisor` 得到的商。

**示例 1：**

>**输入：** dividend = 10, divisor = 3
>**输出：** 3

**示例 2：**

>**输入：** dividend = 7, divisor = -3
>**输出：** -2

**说明：**

- 被除数和除数均为 32 位有符号整数。
- 除数不为 0。
- 假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−2^31,  2^31 − 1]。本题中，如果除法结果溢出，则返回 2^31 − 1。



## 题解

```
class Solution {
    func divide(_ dividend: Int, _ divisor: Int) -> Int {
        let INT_MAX = Int(INT32_MAX)
        if divisor == 0 {
            return INT_MAX
        }
        let flag = (dividend > 0) == (divisor > 0)
        var d1 = abs(dividend), d2 = abs(divisor), count = 0
        while d1 >= d2 {
            var shift = 0
            while d1 >= d2 << shift {
                shift += 1
            }
            d1 -= d2 << (shift - 1)
            count += 1 << (shift - 1)
        }
        if count > INT_MAX && flag {
            return INT_MAX
        }
        return flag ? count : -count
    }
}
```

