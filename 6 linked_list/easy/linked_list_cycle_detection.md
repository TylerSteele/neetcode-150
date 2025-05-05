# [Linked List Cycle Detection](https://neetcode.io/problems/linked-list-cycle-detection)

## 5/4/2025

This one doesn't seem to be too difficult at all, which makes me suspicious that it's more complicated than it seems? I feel like the
constraints should mention the fact that the values don't repeat. But I guess otherwise this would be impossible to solve?

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        visited = []
        current = head
        while current:
            visited.append(current.val)
            if (current.next and current.next.val in visited):
                return True
            current = current.next

        return False
```

Okay, the fast / slow pointer technique is neat. There's no _way_ I would come up with this solution organically. Maybe if I was left alone with this problem for a lifetime. It is really neat and memorable though, so hopefully I think to use it next time.
