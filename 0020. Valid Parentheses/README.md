# 0020. Valid Parentheses

English ｜ [简体中文](README-zh_CN)



## Q

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Example 1:**

>**Input:** "()"
>**Output:** true

**Example 2:**

>**Input:** "()[]{}"
>**Output:** true

**Example 3:**

>**Input:** "(]"
>**Output:** false

**Example 4:**

>**Input:** "([)]"
>**Output:** false

**Example 5:**

>**Input:** "{[]}"
>**Output:** true



## A

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

