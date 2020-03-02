# 0031. Next Permutation

English ｜ [简体中文](./README-zh_CN.md)



## Q

Implement **next permutation**, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be [in-place](http://en.wikipedia.org/wiki/In-place_algorithm) and use only constant extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.

`1,2,3` → `1,3,2`
`3,2,1` → `1,2,3`
`1,1,5` → `1,5,1`



## A

```
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

