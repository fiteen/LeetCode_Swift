# 0031. 下一个排列

[English](./README.md) ｜ 简体中文



##  题目描述

实现获取下一个排列的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。

如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。

必须[原地](https://baike.baidu.com/item/原地算法)修改，只允许使用额外常数空间。

以下是一些例子，输入位于左侧列，其相应输出位于右侧列。

`1,2,3` → `1,3,2`

`3,2,1` → `1,2,3`

`1,1,5` → `1,5,1`



## 题解

```
/** 算法描述：
 *  1. 从后向前查找第一个相邻的升序元素对(i-1, i)，满足 nums[i-1] < nums[i]，此时 [i, end) 必然是降序的；
 *  2. 在 [i, end) 范围内从后向前查找第一个满足 A[i-1] < A[k] 的 k
 *  3. 交换 A[i-1] 和 A[k]
 *  4. 逆置 [i, end)，使其升序
 *  5. 如果步骤 1 中找不到符合的元素对(i-1, i)，说明[begin, end) 为降序，直接跳到步骤 4
 */

class Solution {
    func nextPermutation(_ nums: inout [Int]) {
        let count = nums.count
        if count < 2 {
            return
        }
        var i : Int = count - 1

        while i > 0 {
            if nums[i - 1] < nums[i] {
                var j = count - 1
                while j >= i {
                    if nums[i-1] < nums[j] {
                        swap(&nums, i-1, j)
                        nums = nums[0...i-1] + nums[i...].reversed()
                        return
                    }
                    j -= 1
                }
            }
            i -= 1
            if i == 0 {
                nums.reverse()
                return
            }
        }
    }
    
    func swap(_ nums: inout [Int], _ i: Int, _ j: Int) {
        let temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

