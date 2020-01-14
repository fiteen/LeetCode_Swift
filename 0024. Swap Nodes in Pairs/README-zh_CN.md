# 0024. 两两交换链表的节点

[English](README) ｜ 简体中文



## 题目描述

给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。

**你不能只是单纯的改变节点内部的值**，而是需要实际的进行节点交换。

**示例：**

>给定 1->2->3->4, 你应该返回 2->1->4->3.



## 题解

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

