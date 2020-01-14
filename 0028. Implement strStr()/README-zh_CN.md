# 0028. 实现 strStr()

[English](./README.md) ｜ 简体中文



## 题目描述

实现 [strStr()](http://www.cplusplus.com/reference/cstring/strstr/]) 函数。

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  **-1**。



**示例 1:**

>**输入：** haystack = "hello", needle = "ll"
>**输出：** 2

**Example 2:**

>**输入：** haystack = "aaaaa", needle = "bba"
>**输出：** -1

**说明：**

当 `needle` 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 `needle` 是空字符串时我们应当返回 0 。这与C语言的 [strstr()](https://baike.baidu.com/item/strstr/811469) 以及 Java的 [indexOf()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf(java.lang.String)) 定义相符。



## 题解

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

