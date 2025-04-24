# [Contains Duplicate](https://neetcode.io/problems/duplicate-integer)

## 4/23/2025

This is the beginning, so I'm not able to quickly recall all of the handy algorithms and solutions. My first solution is a basic one, but it works.

```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        duplicates_check = nums.copy()
        for num in nums:
            duplicates_check.remove(num)
            try:
                duplicates_check.remove(num)
            except ValueError:
                continue
            return True
        return False

```

It relies on a try / except block and convenient python functions. It also has time O(n) and space O(n). It's unique in that it's not one of the listed solution, but it's basically solution 3. Hash Set with the disadvantage of copying the entire list instead of initializing an empty set.

## 4/24/2025

My first attempt today is much more typical. I used the hashmap, but I forgot that I didn't need to count occurances. I just need to see if a duplicate exists. Still, it functions the same way as the ideal solution.

```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        occurences = {}
        for num in nums:
            occurences[num] = occurences.get(num, 0) + 1
            if occurences[num] > 1:
                return True
        return False
```
