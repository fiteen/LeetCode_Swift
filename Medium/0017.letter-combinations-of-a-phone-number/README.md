# 0017. Letter Combinations of a Phone Number

English ｜ [简体中文](./README-zh_CN.md)



## Q

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![Telephone-keypad](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**Example:**

>**Input:** "23"
>**Output:** ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.



## A

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

