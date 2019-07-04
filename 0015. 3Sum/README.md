## Q

Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

**Note:**

The solution set must not contain duplicate triplets.

Example:

```
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```


## A

```
class Solution {
    func threeSum(_ nums: [Int]) -> [[Int]] {
        var solution = [[Int]]()
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
                    solution.append([-target, sortedNums[j], sortedNums[k]])
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
        return solution
    }
}
```

