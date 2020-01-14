# 0016. 3Sum Closest

[English](./README.md) ｜ 简体中文



## 题目描述

给定一个包括 n 个整数的数组 `nums` 和 一个目标值 `target`。找出 `nums` 中的三个整数，使得它们的和与 `target` 最接近。返回这三个数的和。假定每组输入只存在唯一答案。

**示例：**

>例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.
>
>与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).
>



## 题解

```
class Solution {
    func threeSumClosest(_ nums: [Int], _ target: Int) -> Int {
        let sortedNums = nums.sorted()
        var res = sortedNums[0] + sortedNums[1] + sortedNums[2]
        for i in 0...sortedNums.count {
            if i - 1 >= 0, i < sortedNums.count, sortedNums[i - 1] == sortedNums[i] {
                continue
            }
            var j = i + 1, k = sortedNums.count - 1
            while j < k {
                let sum = sortedNums[i] + sortedNums[j] + sortedNums[k]
                if abs(sum - target) < abs(res - target) {
                    res = sum
                }
                if sum < target {
                    j += 1
                } else if sum > target {
                    k -= 1
                } else {
                    return res
                }
            }
        }
        return res
    }
}
```

