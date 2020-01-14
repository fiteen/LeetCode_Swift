# 0005. 最长回文子串

[English](README) ｜ 简体中文



## 题目描述

给定一个字符串 `s`，找到 `s` 中最长的回文子串。你可以假设 `s` 的最大长度为 1000。

**示例 1：**

>**输入：**"babad"
>**输出：**"bab"
>**注意：**"aba" 也是一个有效答案。

**示例 2：**

>**输入：**"cbbd"
>**输出：**"bb"



## 题解

```
class Solution {
    func longestPalindrome(_ s: String) -> String {
        if s.count == 0 {
            return ""
        }
        var S = [Character]()
        for c in s {
            S.append(c)
        }
        var startIndex : Int = 0, endIndex : Int = 0
        for (i, _) in s.enumerated()  {
            let addLen = expandCenter(S, i, i)
            let evenLen = expandCenter(S, i, i + 1)
            let len = max(addLen, evenLen)
            if len > endIndex - startIndex {
                startIndex = i - (len - 1) / 2
                endIndex = i + len / 2
            }
        }
        let leftIndex = s.index(s.startIndex, offsetBy: startIndex)
        let rightIndex = s.index(s.startIndex, offsetBy: endIndex + 1)
        let sub = s[leftIndex..<rightIndex]
        return String(sub)
    }
    
    func expandCenter(_ s: [Character], _ left: Int, _ right: Int) -> Int {
        var L : Int = left, R : Int = right
        while  L >= 0 && R < s.count && s[L] == s[R] {
            L -= 1
            R += 1
        }
        return R - L - 1
    }
}
```
