# [Merge Two Sorted Linked Lists](https://neetcode.io/problems/merge-two-sorted-linked-lists)

## 5/3/2025

This seems like it will be a fun one. I need to basically traverse both lists at once, appending the next, lower value.

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        if not list1:
            return list2
        if not list2:
            return list1
        current1 = list1
        current2 = list2
        if current1.val < current2.val:
            head = currentNewList = current1
            current1 = current1.next
        else:
            head = currentNewList = current2
            current2 = current2.next

        while current1 or current2:
            if not current2 or current1 and current1.val < current2.val:
                currentNewList.next = current1
                currentNewList = current1
                current1 = current1.next
            else:
                currentNewList.next = current2
                currentNewList = current2
                current2 = current2.next

        return head
```

So I got it, but my logic is quite a bit more complicated than the posted solution.

I can do a `while _ and _` instead of a `while _ or _` to save some checks. I don't really understand how you're able to set the first node to an empty node. I guess a node without a value isn't really 'counted'? Weird.

I can see that the posted solution is much more concise, but my own solution is much more intuitive to me. Makes sense I guess lol.
