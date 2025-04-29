# [Valid Parentheses](https://neetcode.io/problems/validate-parentheses)

## 4/28/2025

So this one, being in the Stack category, strikes me as a problem I can solve by maintaining a stack of 'open' characters and popping them when I find their 'close' partner. If I ever encounter a mismatched partner, I return False.

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        partners = {')': '(', '}': '{', ']': '['}
        for character in s:
            if character in "({[":
                stack.append(character)
                continue
            if character in ")}]":
                if not stack:
                    return False
                if stack[-1] == partners[character]:
                    stack.pop()
                else:
                    return False
        if stack:
            return False
        return True
```

I managed to complete on my first try (not counting syntax / silly mistakes). And I got O(n) time and O(1) space complexity. Actually, I guess it's worst case scenario O(n) space complexity.
