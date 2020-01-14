# 0002. 两数相加

[English](./README.md) ｜ 简体中文



## 题目描述

给出两个 **非空** 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 **逆序** 的方式存储的，并且它们的每个节点只能存储 **一位** 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

**示例：**

>**输入：**(2 -> 4 -> 3) + (5 -> 6 -> 4)
>**输出：**7 -> 0 -> 8
>**原因：**342 + 465 = 807



## 题解

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public var val: Int
 *     public var next: ListNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.next = nil
 *     }
 * }
 */
class Solution {
    func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        var p1 = l1, p2 = l2, node : ListNode?, pointer : ListNode?
        var flag = 0
        while p1 != nil || p2 != nil || flag == 1  {
            let t1 : Int =  p1?.val ?? 0
            let t2 : Int =  p2?.val ?? 0
            let sum = flag + t1 + t2
            if node == nil {
                node = ListNode(sum % 10);
            } else {
                node?.next = ListNode(sum % 10)
                node = node?.next
            }
            pointer = pointer ?? node
            p1 = p1?.next
            p2 = p2?.next
            flag = sum / 10
        }
        return pointer
    }
}
```
