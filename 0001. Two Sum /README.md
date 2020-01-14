# 0001.Two Sum

English ｜ [简体中文](./README-zh_CN.md)



## Q

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the same element twice.

**Example:**

>Given nums = [2, 7, 11, 15], target = 9,
>
>Because nums[**0**] + nums[**1**] = 2 + 7 = 9,
>return [**0, 1**].



## A

```
class Solution {
    func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
        var dic = [Int: Int]()
        for (i, n) in nums.enumerated() {
            let complement = target - n 
            if dic.keys.contains(complement) && i != dic[complement] {
                return [dic[complement]!, i]
            }
            dic[n] = i
        }
        return [];
    }
}
```
