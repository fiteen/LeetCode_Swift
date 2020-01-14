# 0015. 三数之和

[English](README) ｜ 简体中文



## 题目描述

给定一个包含 n 个整数的数组 `nums`，判断 `nums` 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。

**注意：**答案中不可以包含重复的三元组。

**示例：**

>给定数组 nums = [-1, 0, 1, 2, -1, -4]，
>
>满足要求的三元组集合为：
>[
>  [-1, 0, 1],
>  [-1, -1, 2]
>]



## 题解

```
class Solution {
    func threeSum(_ nums: [Int]) -> [[Int]] {
        var res = [[Int]]()
        let sortedNums = nums.sorted()
        if nums.count < 3 {
            return []
        }
        for i in 0...nums.count - 1 {
            if i > 0, sortedNums[i - 1] == sortedNums[i] {
                continue
            }
            var j = i + 1, k = nums.count - 1
            while j < k {
                let target = -sortedNums[i]
                let sum = sortedNums[j] + sortedNums[k]
                if sum < target {
                    j += 1
                    while j < k, sortedNums[j] == sortedNums[j - 1] {
                        j += 1
                    }
                } else if sum > target {
                    k -= 1
                    while j < k, sortedNums[k] == sortedNums[k + 1] {
                        k -= 1
                    }
                } else {
                    res.append([-target, sortedNums[j], sortedNums[k]])
                    j += 1
                    k -= 1
                    while j < k, sortedNums[j] == sortedNums[j - 1] {
                        j += 1
                    }
                    while j < k, sortedNums[k] == sortedNums[k + 1] {
                        k -= 1
                    }
                }
            }
        }
        return res
    }
}
```

