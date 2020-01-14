# 0028. Implement strStr()

English ｜ [简体中文](./README-zh_CN.md)



## Q

Implement [strStr()](http://www.cplusplus.com/reference/cstring/strstr/]).

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

**Example 1:**

>**Input:** haystack = "hello", needle = "ll"
>**Output:** 2

**Example 2:**

>**Input:** haystack = "aaaaa", needle = "bba"
>**Output:** -1

**Clarification:**

What should we return when `needle` is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when `needle` is an empty string. This is consistent to C's [strstr()](http://www.cplusplus.com/reference/cstring/strstr/) and Java's [indexOf()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf(java.lang.String)).



## A

```
class Solution {
    func strStr(_ haystack: String, _ needle: String) -> Int {
        let nCount = needle.count
        if nCount == 0 {
            return 0
        }
        let haystackArr = Array(haystack), hCount = haystack.count
        let needleArr = Array(needle)
        var i = 0, j = 0
        while j < nCount && i + j < hCount {
            if haystackArr[i + j] == needleArr[j] {
                if  j == nCount - 1 {
                    return i
                } else {
                    j += 1
                }
            } else {
                j = 0
                i += 1
            }
        }
        return -1
    }
}
```

