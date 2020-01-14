# 0024. Swap Nodes in Pairs

English ｜ [简体中文](README-zh_CN)



## Q

Given a linked list, swap every two adjacent nodes and return its head.

You may **not** modify the values in the list's nodes, only nodes itself may be changed.

**Example:**

>Given 1->2->3->4, you should return the list as 2->1->4->3.



## A

```
class Solution {
    func swapPairs(_ head: ListNode?) -> ListNode? {
        if head == nil || head?.next == nil {
            return head
        }
        let next = head?.next
        head?.next = swapPairs(next?.next)
        next?.next = head
        return next
    }
}
```

