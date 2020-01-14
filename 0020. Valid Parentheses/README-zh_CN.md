# 0020. 有效的括号

[English](README) ｜ 简体中文



## 题目描述

给定一个只包括 `'('`，`')'`，`'{'`，`'}'`，`'['`，`']'` 的字符串，判断字符串是否有效。

有效字符串需满足：

1. 左括号必须用相同类型的右括号闭合。
2. 左括号必须以正确的顺序闭合。

注意空字符串可被认为是有效字符串。

**示例 1：**

>**输入：** "()"
>**输出：** true

**示例 2：**

>**输入：** "()[]{}"
>**输出：** true

**示例 3：**

>**输入：** "(]"
>**输出：** false

**示例 4：**

>**输入：** "([)]"
>**输出：** false

**示例 5：**

>**输入：** "{[]}"
>**输出：** true



## 题解

```
class Solution {
    func isValid(_ s: String) -> Bool {
        var str : [Character] = []
        for c in s {
            if str.count == 0 {
                str.append(c)
                continue
            }
            let combine = String(str.last!) + String(c)
            if combine == "[]" || combine == "{}" || combine == "()" {
                str.removeLast()
            } else {
                str.append(c)
            }
        }
        return str.count == 0
    }
}
```

