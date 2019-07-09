## Q

Given a linked list, remove the n-th node from the end of list and return its head.

Example:

```
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
```

**Note:**

Given n will always be valid.

**Follow up:**

Could you do this in one pass?


## A

```
class Solution {
    func removeNthFromEnd(_ head: ListNode?, _ n: Int) -> ListNode? {
        let p = ListNode(0)
        p.next = head
        var q = p, r = p
        for _ in 0..<n {
            q = q.next!
        }
        while q.next != nil {
            q = q.next!
            r = r.next!
        }
        r.next = r.next?.next
        return p.next
    }
}
```

