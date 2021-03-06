# 0009. 回文数

[English](./README.md) ｜ 简体中文



## 题目描述

判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

**示例 1：**

> **输入：**121
> **输出：**true

**示例 2：**

>**输入：**-121
>**输出：**false
>**解释：**从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。

**示例 3：**

>**输入：**10
>**输出：**false
>**解释：**从右向左读, 为 01 。因此它不是一个回文数。

**进阶:**

你能不将整数转为字符串来解决这个问题吗？



## 题解

```
class Solution {
    func isPalindrome(_ x: Int) -> Bool {
        if x < 0 || x != 0 && x % 10 == 0 {
            return false
        }
        var palindrome = 0, y = x
        while palindrome < y {
            palindrome = y % 10 + palindrome * 10
            y /= 10
        }
        return y == palindrome || y == palindrome / 10
    }
}
```
