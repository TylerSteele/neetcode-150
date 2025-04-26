# [Valid Anagram](https://neetcode.io/problems/is-anagram)

## 4/23/2025

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

## 4/25/2025

It's funny that I'm back to this after doing the palindrome problem. I know I should be using a hash, but I think I'm getting confused with another solution. Contains duplicate, probably. I think I got it now, just create two hashes and count all of the letters? That doesn't _feel_ like the most efficient solution, though. Hmm.

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        character_hash_s = {}
        character_hash_t = {}
        for i in range(0, len(s)):
            character_hash_s[s[i]] = character_hash_s.get(s[i], 0) + 1
            character_hash_t[t[i]] = character_hash_t.get(t[i], 0) + 1
        return character_hash_s == character_hash_t

```

I remembered to use `.get` this time as opposed to the defaultdict, which is a bit of an improvement I suppose. Oh, actually my new solution is much better because it avoids `.replace` :clap:

I'm looking at the 3. Hash Table (Using Array) solution and that one is really wild to me. I need to expose myself more to that thinking, I like the idea of keeping 'score' by adding 1 in case A and subtracting 1 in case B, passing only on a value of 0. Let's see if I can remember this for next time.
