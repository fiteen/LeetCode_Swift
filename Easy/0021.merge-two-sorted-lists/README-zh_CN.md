# 0021. 合并两个有序链表

[English](./README.md) ｜ 简体中文



## 题目描述

将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

**示例：**

>**输入：** 1->2->4, 1->3->4
>**输出：** 1->1->2->3->4->4



## 题解

```
class Solution {
    func mergeTwoLists(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        var p = ListNode(-1)
        var ll1 = l1, ll2 = l2
        let q = p
        while ll1 != nil && ll2 != nil {
            if ll1!.val < ll2!.val {
                p.next = ll1
                ll1 = ll1?.next
            } else {
                p.next = ll2
                ll2 = ll2?.next
            }
            p = p.next!
        }
        p.next = ll1 == nil ? ll2 : ll1
        return q.next
    }
}
```

