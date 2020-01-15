# 0018. 4Sum

English ｜ [简体中文](./README-zh_CN.md)



## Q

Given an array `nums` of *n* integers and an integer `target`, are there elements *a*, *b*, *c*, and *d* in `nums` such that *a* +*b* + *c* + *d* = `target`? Find all unique quadruplets in the array which gives the sum of `target`.

**Note:**

The solution set must not contain duplicate quadruplets.

**Example:**

>Given array nums = [1, 0, -1, 0, -2, 2], and target = 0.
>
>A solution set is:
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

