# 0022. Generate Parentheses

English ｜ [简体中文](./README-zh_CN.md)



## Q

Given *n* pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given *n* = 3, a solution set is:

>[
>	"((()))",
>	"(()())",
>	"(())()",
>	"()(())",
>	"()()()"
>]



## A

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

