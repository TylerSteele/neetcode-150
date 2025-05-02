# [Reverse Linked List](https://neetcode.io/problems/reverse-a-linked-list)

## 5/2/2025

This one seems very easy. I don't know if there's a trick to it, maybe there's a way to do it with O(1) space complexity? Let's see.

The description doesn't seem to match the example input and output? Am I returning the entire list, or the "new beginning of the list"?

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        previous = None
        current = head

        while current and current.next:
            new_current = current.next
            current.next = previous
            previous = current
            current = new_current

        if current:
            current.next = previous

        return current
```

I got the iterative O(1) solution the first time, which is nice! I could optimize it slightly by doing `while current` instead of `while current and current.next`, removing the need for that final `if` check. One thing that tripped me up is I was doing `if previous: current.next = previous`, but that meant the tail of my returned list didn't clear its next. My returned list infinitely looped at the end, which meant the site was telling me there was an infinite loop in my code. I interpreted this to mean my loop ran infinitely, which confounded me. I had to paste the code in a python document and run it in my terminal to learn my mistake (the site doesn't show you stdout if there's an infinite loop).
