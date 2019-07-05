## Q

Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

Example:

```
Given array nums = [-1, 2, 1, -4], and target = 1.

The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```


## A

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

