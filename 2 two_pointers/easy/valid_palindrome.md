# [Valid Palindrome](https://neetcode.io/problems/is-palindrome)

## 4/25/2025

Now we are actually doing the palindrome problem. And the examples _don't_ include 'racecar' :unamused:

Anyway, the fact that this is a 'two pointer' problem really gives the solution away, I think? Start at each end string one. Compare both to the opposite in the other string. If they match, move in the pointers... Let's see. It's slightly annoying that the check needs to be case insensitive and ignore special characters in this case. Not sure what that adds to the challenges besides making it more of a pain.

Oh, I'm realizing now that there's only one string. Duh. Well, it's the same idea. And that does sort of explain the case insensitivity and special character exceptions.

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        start = 0
        end = len(s) - 1

        while end > start:
            skip_start = not s[start].isalnum()
            skip_end = not s[end].isalnum()
            if skip_start or skip_end:
                if skip_start: start += 1
                if skip_end: end -= 1
                continue

            if (s[start].upper() != s[end].upper()):
                return False
            end -= 1
            start += 1

        return True
```

Looking good I think? The optimization of combining skip_start and skip_end checks into one condition feels a bit extra, but it prevents redundant loops so I think it's fine. I believe this is O(n) time and O(1).

Okay, in the video he says using the built-in `isalphanum` function is 'cheating'. I mean... I guessss. Let's see if I remember that when I come back to this. He also uses nested while loops to continue moving the pointers. I don't think that's more efficient in practice, but I don't hate it.
