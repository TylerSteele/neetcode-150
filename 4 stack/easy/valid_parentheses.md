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

## 5/2/2025

Okay, this is the stack one. I don't think I'll have any problems?

I got tripped up on some careless mistakes. And then I forgot to return False if the stack still had characters in it. But besides that, pretty smooth.

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        pairs = {'(': ')', '[': ']', '{': '}'}
        for character in s:
            if character in pairs:
                stack.append(character)
            elif character in pairs.values():
                if stack and pairs[stack[-1]] == character:
                    stack.pop()
                else:
                    return False

        return not stack
```

Oh I didn't realize that the only valid characters were the bracket characters. Mine should work on any string that may contain them, so that's nice I guess. Should probably read it next time!
