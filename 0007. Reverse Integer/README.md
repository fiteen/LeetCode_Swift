# 0007. Reverse Integer

English ｜ [简体中文](./README-zh_CN.md)



## Q

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**

>**Input:** 123
>**Output:** 321

**Example 2:**

>**Input:** -123
>**Output:** -321

**Example 3:**

>**Input:** 120
>**Output:** 21

**Note:**

Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−2^31,  2^31 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.



## A

```
class Solution {
    func reverse(_ x: Int) -> Int {
        var n = 0, y = x
        while y != 0 {
            let pop = y % 10
            y /= 10
            if n > INT32_MAX / 10 || (n == INT32_MAX / 10 && pop > 7) {
                return 0
            }
            if n < (-INT32_MAX - 1) / 10 || (n == (-INT32_MAX - 1) / 10 && pop < -8) {
                return 0
            }
            n = 10 * n + pop
        }
        return n
    }
}
```
