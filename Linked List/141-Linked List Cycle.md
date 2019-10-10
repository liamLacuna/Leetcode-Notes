## 141. Linked List Cycle

#### Given a linked list, determine if it has a cycle in it.

#### To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

#

## Solution

#### Brute-force && HashTable
##### O(n) Time, O(n) Space
```
public class Solution {
    public boolean hasCycle(ListNode head) {
        Set<ListNode> set = new HashSet<>();
        while(head != null) {
            if(!set.contains(head)) {
                set.add(head);
                head = head.next;
            }
            else
                return true;
        }
        return false;
    }
}
```

#### Two Pointer
##### O(n) Time, O(1) Space, if it's cycle, the fast pointer would eventually equal to the slow one.
```
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head == null || head.next == null) return false;

        slow = head.next;
        fast = head.next.next;
        while(slow != next){
            if(fast == null || fast.next == null) 
                return false;
            slow = slow.next;
            fast = fast.next.next;
        }
        return true;
    }
}
```