# [Valid Anagram](https://neetcode.io/problems/is-anagram)

I have a bone to pick with this one, because while it is about checking anagrams, the first example word is "racecar". Racecar! Perhaps the most well known palindrome. So my first solution was actually trying check if two strings are palindromes...

For this one, I actually thought of the sorting solution first, but it seemed so cheap that it's like circumventing the problem. I imagine in an interview setting, they would immediately say "Okay, but what would you do if sorting wasn't allowed?" I didn't think about the fact that sorting requires O(1) space complexity, though, which is nice.

Also, I totally missed the fact that these strings could only contain lowercase English letters. I like the solution that uses this information and I should pay more attention next time.

Here's my code:

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        s_contains_map = defaultdict(lambda: 0)
        t_contains_map = defaultdict(lambda: 0)
        modified_t = t
        for letter in s:
            if letter in modified_t:
                s_contains_map[letter] += 1
                t_contains_map[letter] += 1
                modified_t = modified_t.replace(letter, "", 1)
            else:
                return False
        return s_contains_map == t_contains_map

```

Because I use the replace function to modify the string on the fly, I believe the complexity jumps to O(n^2). I also create defaultdicts where using `.get` should've been sufficient. Some of my learnings will just be remembering certain python features. Although it looks like defaultdict is negligible in terms of complexity.

The biggest failure with this solution is to not recognize that the counts could be added to the existing values.
