## Q

Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

Example:

```
Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
```


## A

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

