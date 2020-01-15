# 0017. 电话号码的字母组合

[English](./README.md) ｜ 简体中文



## 题目描述

给定一个仅包含数字 `2-9` 的字符串，返回所有它能表示的字母组合。

给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

![Telephone-keypad](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**示例:**

>**输入：**"23"
>**输出：**["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

**说明:**

尽管上面的答案是按字典序排列的，但是你可以任意选择答案输出的顺序。



## 题解

```
class Solution {
    func letterCombinations(_ digits: String) -> [String] {
        let map: [Character : String] = ["2": "abc", "3": "def", "4": "ghi", "5": "jkl", "6": "mno", "7": "pqrs", "8": "tuv", "9":"wxyz"]
        var res : [String] = []
        for c in digits {
            let temp = res
            res.removeAll()
            for s in map[c]! {
                if temp.count == 0 {
                    res.append(String(s))
                } else {
                    for t in temp {
                        var a = t
                        a.append(s)
                        res.append(a)
                    }
                }
            }
        }
        return res
    }
}
```

