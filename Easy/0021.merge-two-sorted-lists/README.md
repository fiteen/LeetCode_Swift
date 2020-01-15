# 0021. Merge Two Sorted Lists

English ｜ [简体中文](./README-zh_CN.md)



## Q

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

>**Input:** 1->2->4, 1->3->4
>**Output:** 1->1->2->3->4->4



## A

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

