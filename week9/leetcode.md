### 21. Merge Two Sorted Lists
>Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

>Example:

>Input: 1->2->4, 1->3->4
>Output: 1->1->2->3->4->4

#### One Solution
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if (l1 == null) return l2;
        if (l2 == null) return l1;
        ListNode head = null;
        ListNode t1 = l1;
        ListNode t2 = l2;
        ListNode p1 = t1;
        ListNode p2 = t2;
        while (t1 != null && t2 != null){
            if (head == null){
                head = (l1.val <= l2.val) ? l1: l2;
            }
            if (t1.val <= t2.val){
                while (t1.val <= t2.val){
                    p1 = t1;
                    t1 = t1.next;
                    if (t1 == null)
                        break;
                }
                p1.next = t2;
            }
            if (t1 == null)
                break;
            if (t1.val > t2.val){
                while (t1.val > t2.val){
                    p2 = t2;
                    t2 = t2.next;
                    if (t2 == null)
                        break;
                }
                p2.next = t1;
            }
        }
        return head;
    }
}
```
score:
```
Runtime: 0 ms, faster than 100.00% of Java online submissions for Merge Two Sorted Lists.
Memory Usage: 35.8 MB, less than 99.93% of Java online submissions for Merge Two Sorted Lists.
```

#### note
made a mistake: `p1.next = t2;` misplaced in the `while` brackets 