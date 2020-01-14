# 0029. Divide Two Integers

English ｜ [简体中文](README-zh_CN)



## Q

Given two integers `dividend` and `divisor`, divide two integers without using multiplication, division and mod operator.

Return the quotient after dividing `dividend` by `divisor`.

The integer division should truncate toward zero.

**Example 1:**

>**Input:** dividend = 10, divisor = 3
>**Output:** 3

**Example 2:**

>**Input:** dividend = 7, divisor = -3
>**Output:** -2

**Note:**

- Both dividend and divisor will be 32-bit signed integers.
- The divisor will never be 0.
- Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−2^31,  2^31 − 1]. For the purpose of this problem, assume that your function returns 2^31 − 1 when the division result overflows.



## A

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

