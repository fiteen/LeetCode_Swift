# 0005. Longest Palindromic Substring 

English ｜ [简体中文](./README-zh_CN.md)


## Q

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example 1:**

>**Input:** "babad"
>**Output:** "bab"
>**Note:** "aba" is also a valid answer.

**Example 2:**

>**Input:** "cbbd"
>**Output:** "bb"



## A

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
