# 0010. Regular Expression Matching

English ｜ [简体中文](./README-zh_CN.md)



## Q

Given an input string (`s`) and a pattern (`p`), implement regular expression matching with support for `'.'` and `'*'`.

>'.' Matches any single character.
>'*' Matches zero or more of the preceding element.
>The matching should cover the **entire** input string (not partial).

**Note:**

- `s` could be empty and contains only lowercase letters `a-z`.
- `p` could be empty and contains only lowercase letters `a-z`, and characters like `.` or `*`.

**Example 1:**

>**Input:**
>s = "aa"
>p = "a"
>**Output:** false
>**Explanation:** "a" does not match the entire string "aa".

**Example 2:**

>**Input:**
>s = "aa"
>p = "a\*"
>**Output:** true
>**Explanation:** '*' means zero or more of the precedeng element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".

**Example 3:**

>**Input:**
>s = "ab"
>p = ".\*"
>**Output:** true
>**Explanation:** ".\*" means "zero or more (*) of any character (.)".

**Example 4:**

>**Input:**
>s = "aab"
>p = "c*a*b"
>**Output:** true
>Explanation: c can be repeated 0 times, a can be repeated 1 time. Therefore it matches "aab".

**Example 5:**

>**Input:**
>s = "mississippi"
>p = "mis\*is\*p\*."
>**Output:** false



## A

```
class Solution {
    func isMatch(_ s: String, _ p: String) -> Bool {
        if p.isEmpty {
            return s.isEmpty
        }
        let sArr = Array(s), pArr = Array(p)
        let isFirstMatch : Bool = (!s.isEmpty) && (pArr[0] == sArr[0] || pArr[0] == ".")
        if (pArr.count >= 2 && pArr[1] == "*") {
            return isFirstMatch && isMatch(String(s.suffix(s.count - 1)), p) || isMatch(s, String(p.suffix(p.count - 2)))
        } else {
            return isFirstMatch && isMatch(String(s.suffix(s.count - 1)), String(p.suffix(p.count - 1)))
        }
    }
}
```
