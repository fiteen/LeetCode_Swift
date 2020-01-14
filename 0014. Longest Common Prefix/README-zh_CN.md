# 0014. 最长公共前缀

[English](README) ｜ 简体中文



## 题目描述

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 `""`。

**示例 1：**

>**输入：** ["flower","flow","flight"]
>**输出：** "fl"

**示例 2：**

>**输入：** ["dog","racecar","car"]
>**输出：** ""
>**解释：** 输入不存在公共前缀。

**说明：**

所有输入只包含小写字母 `a-z` 。



## 题解

```
class Solution {
    func longestCommonPrefix(_ strs: [String]) -> String {
        if strs.count == 0 {
            return ""
        }
        var p = strs[0]
        if strs.count == 1 {
            return p
        }
        for i in 1...strs.count - 1 {
            let s = strs[i]
            while s.prefix(p.count) != p {
                p = String(p.prefix(p.count - 1))
                if p.isEmpty {
                    return ""
                }
            }
        }
        return p
    }
}
```
