<img src="https://skillicons.dev/icons?i=python" align="right" />

# Python Default Solution - Leetcode

```python3
class Solution:
    def kWeakestRows(self, mat: List[List[int]], k: int) -> List[int]:
        def nth_element(nums, n, compare=lambda a, b: a < b):
            def partition_around_pivot(left, right, pivot_idx, nums, compare):
                new_pivot_idx = left
                nums[pivot_idx], nums[right] = nums[right], nums[pivot_idx]
                for i in range(left, right):
                    if compare(nums[i], nums[right]):
                        nums[i], nums[new_pivot_idx] = nums[new_pivot_idx], nums[i]
                        new_pivot_idx += 1

                nums[right], nums[new_pivot_idx] = nums[new_pivot_idx], nums[right]
                return new_pivot_idx

            left, right = 0, len(nums) - 1
            while left <= right:
                pivot_idx = random.randint(left, right)
                new_pivot_idx = partition_around_pivot(left, right, pivot_idx, nums, compare)
                if new_pivot_idx == n:
                    return
                elif new_pivot_idx > n:
                    right = new_pivot_idx - 1
                else:
                    left = new_pivot_idx + 1
        
        nums = [(sum(mat[i]), i) for i in range(len(mat))]
        nth_element(nums, k)
        return map(lambda x: x[1], sorted(nums[:k]))
```
