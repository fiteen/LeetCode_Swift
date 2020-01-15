# 0022. 括号生成

[English](./README.md) ｜ 简体中文



## 题目描述

给出 *n* 代表生成括号的对数，请你写出一个函数，使其能够生成所有可能的并且**有效的**括号组合。

例如，给出 *n* = 3，生成结果为：

>[
>  	"((()))",
>  	"(()())",
>  	"(())()",
>  	"()(())",
>  	"()()()"
>]



## 题解

```
class Solution {
    func generateParenthesis(_ n: Int) -> [String] {
        var res: [String] = []
        if n == 0 {
            res.append("")
        } else {
            for i in 0...n-1 {
                for left in generateParenthesis(i) {
                    for right in generateParenthesis(n-i-1) {
                        res.append("(" + left + ")" + right)
                    }
                }
            }
        }
        return res
    }
}
```

