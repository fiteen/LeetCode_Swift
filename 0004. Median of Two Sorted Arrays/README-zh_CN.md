# 0004. 寻找两个有序数组的中位数

[English](README) ｜ 简体中文



## 题目描述

给定两个大小为 m 和 n 的有序数组 `nums1` 和 `nums2`。

请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。

你可以假设 `nums1` 和 `nums2` 不会同时为空。

**示例 1：**

>nums1 = [1, 3]
>nums2 = [2]
>
>则中位数是 2.0

**示例 2：**

>nums1 = [1, 2]
>nums2 = [3, 4]
>
>则中位数是 (2 + 3)/2 = 2.5



## 题解

```
class Solution {
    func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
        var m : Int = nums1.count, n : Int = nums2.count
        var A : [Int] = nums1, B : [Int] = nums2
        if m > n {
            let temp : [Int] = A
            A = B
            B = temp
            let t : Int = m
            m = n
            n = t
        }
        let halfLength : Int = (m + n + 1) / 2
        var iMin : Int = 0, iMax : Int = m
        while iMin <= iMax {
            let i : Int = (iMin + iMax) / 2
            let j = halfLength - i
            if i < iMax && A[i] < B[j - 1] {
                iMin = i + 1
            } else if i > iMin && B[j] < A[i - 1] {
                iMax = i - 1
            } else {
                var leftMax : Int, rightMin : Int
                if i == 0 {
                    leftMax = B[j - 1]
                } else if j == 0 {
                    leftMax = A[i - 1]
                } else {
                    leftMax = max(A[i - 1], B[j - 1])
                }
                if (m + n) % 2 == 1 {
                    return Double(leftMax)
                }
                if (i == m) {
                    rightMin = B[j]
                } else if (j == n) {
                    rightMin = A[i]
                } else {
                    rightMin = min(A[i], B[j])
                }
                return Double(leftMax + rightMin) / 2
            }
        }
        return 0.0
    }
}
```
