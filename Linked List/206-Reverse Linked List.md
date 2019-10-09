## 206. Reverse Linked List

#### Reverse a singly linked list.

```
Example: 
Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL
```

# 

## Solution

#### Iterative
O(1)space, O(n)Time
```
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode current = head;
        ListNode prev = null;
        while(current!= null){
            ListNode temp = current.next;
            current.next = prev;
            prev = current;
            current = temp;
        }
        return prev;
    }
}
```

#### Recursive
O(n)space, O(n)Time
```
class Solution {
    public listNode reverseList(listNode head) {
        if(head == null || head.next == null) return head;
        ListNode pointer = reverseList(head.next);
        head.next.next = head;
        head.next = null;
        return pointer;
    }
}
```
