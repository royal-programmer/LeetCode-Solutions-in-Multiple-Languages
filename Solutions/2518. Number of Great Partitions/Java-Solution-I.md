<img src="https://skillicons.dev/icons?i=java" align="right" />

# Java Default Solution - Leetcode

```java
class Solution {
    public int countPartitions(int[] nums, int k) {
        int n = nums.length, mod = 1000000007;
        long totSum = 0;
        for (int x : nums) {
            totSum += x;
        }
        if (totSum < (long) (k + k)) {
            return 0;
        }
        int[][] dp = new int[n + 1][k + 1];
        dp[0][0] = 1;

        for (int i = 0; i <= n; i++) {
            for (int j = 0; j <= k; j++) {
                if (j == 0) {
                    dp[i][j] = 1;
                } else if (i > 0 && j > 0) {
                    dp[i][j] = dp[i - 1][j];
                    if (j >= nums[i - 1]) {
                        dp[i][j] += dp[i - 1][j - nums[i - 1]];
                        dp[i][j] %= mod;
                    }
                }
            }
        }
        int invalidWays = 0;
        for (int j = 0; j < k; j++) {
            invalidWays += dp[n][j];
            invalidWays %= mod;
        }
        invalidWays *= 2;
        invalidWays %= mod;
        int totalWays = 1;
        for (int i = 1; i <= n; i++) {
            totalWays *= 2;
            totalWays %= mod;
        }
        int ans = (int) ((totalWays - invalidWays + mod) % mod);
        return ans;
    }
}
```
