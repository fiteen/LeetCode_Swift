# 0003. Longest Substring Without Repeating Characters

English ｜ [简体中文](./README-zh_CN.md)



## Q

Given a string, find the length of the **longest substring** without repeating characters.

**Example 1:**

> **Input:** "abcabcbb"
> **Output:** 3 
> **Explanation:** The answer is "abc", with the length of 3. 

**Example 2:**

>**Input:** "bbbbb"
>**Output:** 1
>**Explanation:** The answer is "b", with the length of 1.

Example 3:

>**Input:** "pwwkew"
>**Output:** 3
>**Explanation:** The answer is "wke", with the length of 3. 
>             Note that the answer must be a **substring**, "pwke" is a subsequence and not a substring.



## A

```
class Solution {
    func lengthOfLongestSubstring(_ s: String) -> Int {
        var chars = [Character: Int]()
        var length : Int = 0
        var i : Int = 0
        for (j, ch) in s.enumerated() {
            if let head = chars[ch] {
                i = max(head + 1, i)
            }
            chars[ch] = j
            length = max(j - i + 1, length)
        }
        return length
    }
}
```
