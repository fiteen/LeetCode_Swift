# 0018. 四数之和

[English](./README.md) ｜ 简体中文



## 题目描述

给定一个包含 *n* 个整数的数组 `nums` 和一个目标值 `target`，判断 `nums` 中是否存在四个元素 *a*，*b*，*c* 和 *d* ，使得 *a* + *b* + *c* + *d* 的值与 `target` 相等？找出所有满足条件且不重复的四元组。

**注意：**

答案中不可以包含重复的四元组。

**示例：**

>给定数组 nums = [1, 0, -1, 0, -2, 2]，和 target = 0。
>
>满足要求的四元组集合为：
>[
>  [-1,  0, 0, 1],
>  [-2, -1, 1, 2],
>  [-2,  0, 0, 2]
>]



## A

```
class Solution {
    func fourSum(_ nums: [Int], _ target: Int) -> [[Int]] {
        let sortNums = nums.sorted()
        var res : [[Int]] = []
        if nums.count < 4 {
            return []
        }
        for i in 0...sortNums.count - 4 {
            if i != 0 && sortNums[i - 1] == sortNums[i] {
                continue
            }
            for j in i + 1...sortNums.count - 2 {
                if j != i + 1 && sortNums[j - 1] == sortNums[j] {
                    continue
                }
                var k = j + 1, l = sortNums.count - 1
                while k < l {
                    let sum = sortNums[i] + sortNums[j] + sortNums[k] + sortNums[l]
                    if sum < target {
                        k += 1
                        while k < l, sortNums[k] == sortNums[k - 1] {
                            k += 1
                        }
                    } else if sum > target{
                        l -= 1
                        while k < l, sortNums[l] == sortNums[l + 1] {
                            l -= 1
                        }
                    } else {
                        res.append([sortNums[i], sortNums[j], sortNums[k], sortNums[l]])
                        k += 1
                        l -= 1
                        while k < l, sortNums[k] == sortNums[k - 1] {
                            k += 1
                        }
                        while k < l, sortNums[l] == sortNums[l + 1] {
                            l -= 1
                        }
                    }
                }
            }
        }
        return res
    }
}
```

