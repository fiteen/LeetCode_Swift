## Q

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume nums1 and nums2 cannot be both empty.

Example 1:

```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```

Example 2:

```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```


## A

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
