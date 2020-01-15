# 0023. 合并K个排序链表

[English](./README.md) ｜ 简体中文



## 题目描述

合并 *k* 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

**示例：**

>**输入：**
>[
>  	1->4->5,
>  	1->3->4,
>  	2->6
>]
>**输出：** 1->1->2->3->4->4->5->6



## 题解

```
class Solution {
    func mergeKLists(_ lists: [ListNode?]) -> ListNode? {
        var vals = [Int]()
        for list in lists {
            var p = list
            while p != nil {
                vals.append(p!.val)
                p = p!.next
            }
        }
        vals.sort()
        var q : ListNode = ListNode(Int.min)
        let res = q
        for val in vals {
            q.next = ListNode(val)
            q = q.next!
        }
        return res.next
    }
}
```

