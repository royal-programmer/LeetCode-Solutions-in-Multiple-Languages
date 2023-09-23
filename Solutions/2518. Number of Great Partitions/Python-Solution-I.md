<img src="https://skillicons.dev/icons?i=python" align="right" />

# Python Default Solution - Leetcode

```python3
class Solution:
    def countPartitions(self, nums: List[int], k: int) -> int:
        n = len(nums)
        mod = 1000000007
        totSum = 0
        for x in nums:
            totSum += x
        if totSum < (k + k):
            return 0
        dp = [[0] * (k + 1) for _ in range(n + 1)]
        dp[0][0] = 1
        for i in range(n + 1):
            for j in range(k + 1):
                if j == 0:
                    dp[i][j] = 1
                elif i > 0 and j > 0:
                    dp[i][j] = dp[i - 1][j]
                    if j >= nums[i - 1]:
                        dp[i][j] += dp[i - 1][j - nums[i - 1]]
                        dp[i][j] %= mod
        invalidWays = 0
        for j in range(k):
            invalidWays += dp[n][j]
            invalidWays %= mod
        invalidWays *= 2
        invalidWays %= mod
        totalWays = 1
        for i in range(1, n + 1):
            totalWays *= 2
            totalWays %= mod
        ans = (totalWays - invalidWays + mod) % mod
        return ans
```
