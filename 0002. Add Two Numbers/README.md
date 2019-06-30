## Q

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```


## A

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
