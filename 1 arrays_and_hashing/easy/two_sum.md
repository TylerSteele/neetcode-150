# [Two Sum](https://neetcode.io/problems/two-integer-sum)

## 4/24/2025

Because the suggestion for time and space complexity for this one was O(n), I avoided sorting in my first solution. This was silly, though, because I ended up with the brute force approach which is O(n^2). I did have fun getting it working with recursion, even though it's a bit extra in this case.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        addend_1_index = 0

        while (result := checkSum(addend_1_index, nums, target)) == None and addend_1_index < len(nums):
            if addend_1_index == len(nums) - 1:
                break
            addend_1_index += 1
        return result

def checkSum(addend_1_index: int, nums: List[int], target: int) -> List[int] | None:
    addend_2_index = addend_1_index + 1
    while nums[addend_1_index] + nums[addend_2_index] != target and addend_2_index < len(nums):
        if addend_2_index == len(nums) - 1:
            break
        addend_2_index += 1
    if nums[addend_1_index] + nums[addend_2_index] == target:
        return [addend_1_index, addend_2_index]
    return None
```

I did watch [this video](https://www.youtube.com/watch?v=aHZW7TuY_yo) after watching the solution video, and realized that I should probably incorporate more repetition in my approach. It's daunting given the number of problems, but it's gotta be a better investment to properly remember the approaches and more deeply understand the problems.

In this example, I didn't think to use the hash map and that wasn't intuitive to me whatsoever. But next time it probably would be! The hash map solution is so elegant.

I also want to start recording my thought process before solving the problem so I can reflect on mental traps I fall into / things I missed.
