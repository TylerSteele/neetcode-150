# [Binary Search](https://neetcode.io/problems/binary-search)

## 5/1/2025

I am very familiar with binary search so this one was easy for me. I did encounter my fair share of off by one errors, though.

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        return binary_search(nums, target, 0, len(nums) - 1)

def binary_search(nums: List[int], target: int, start_index: int, stop_index: int) -> int:
    if start_index > stop_index:
        return -1

    check_index = start_index + (stop_index - start_index) // 2
    if target == nums[check_index]:
        return check_index
    if target > nums[check_index]:
        return binary_search(nums, target, check_index + 1, stop_index)
    return binary_search(nums, target, start_index, check_index - 1)
```

One thing I didn't anticipate was the O(logn) space complexity that you get by making this a recursive function. I'll try to remember to use the iterative approach next time to get those savings.
