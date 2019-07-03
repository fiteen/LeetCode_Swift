## Q

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

```
Input: ["flower","flow","flight"]
Output: "fl"
```

Example 2:

```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Note:**

All given inputs are in lowercase letters a-z.


## A

```
class Solution {
    func longestCommonPrefix(_ strs: [String]) -> String {
        if strs.count == 0 {
            return ""
        }
        var p = strs[0]
        if strs.count == 1 {
            return p
        }
        for i in 1...strs.count - 1 {
            let s = strs[i]
            while s.prefix(p.count) != p {
                p = String(p.prefix(p.count - 1))
                if p.isEmpty {
                    return ""
                }
            }
        }
        return p
    }
}
```
