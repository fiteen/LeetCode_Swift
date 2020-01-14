# 0006. ZigZag Conversion

English ｜ [简体中文](README-zh_CN)


## Q

The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string s, int numRows);
```

**Example 1:**

```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

**Example 2:**

```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I
```


## A

```
class Solution {
    func convert(_ s: String, _ numRows: Int) -> String {
        if numRows == 1 {
            return s
        }
        let zCount = 2 * numRows - 2
        var list : Dictionary = [Int:String]()
        for (i, c) in s.enumerated() {
            let index = i % zCount >= numRows ? zCount - i % zCount : i % zCount
            var rowContent : String = list[index] ?? ""
            rowContent.append(c)
            list[index] = rowContent
        }
        var newS : String = ""
        for i in 0...list.count {
            newS += list[i] ?? ""
        }
        return newS
    }
}
```
