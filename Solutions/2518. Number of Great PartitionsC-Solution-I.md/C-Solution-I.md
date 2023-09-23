<img src="https://skillicons.dev/icons?i=c" align="right" />

# C Default Solution - Leetcode

```
#include <stdio.h>

long long int countPartitions(int* nums, int numsSize, int k) {
    int n = numsSize;
    long long int mod = 1000000007;
    long long int totSum = 0;
    for (int i = 0; i < n; i++) {
        totSum += nums[i];
    }
    
    if (totSum < (k + k)) {
        return 0;
    }
    
    long long int dp[n + 1][k + 1];
    for (int i = 0; i <= n; i++) {
        for (int j = 0; j <= k; j++) {
            dp[i][j] = 0;
        }
    }
    
    dp[0][0] = 1;
    
    for (int i = 0; i <= n; i++) {
        for (int j = 0; j <= k; j++) {
            if (j == 0) {
                dp[i][j] = 1;
            }
            else if (i > 0 && j > 0) {
                dp[i][j] = dp[i - 1][j];
                if (j >= nums[i - 1]) {
                    dp[i][j] += dp[i - 1][j - nums[i - 1]];
                    dp[i][j] %= mod;
                }
            }
        }
    }
    
    long long int invalidWays = 0;
    
    for (int j = 0; j < k; j++) {
        invalidWays += dp[n][j];
        invalidWays %= mod;
    }
    
    invalidWays *= 2;
    invalidWays %= mod;
    
    long long int totalWays = 1;
    
    for (int i = 1; i <= n; i++) {
        totalWays *= 2;
        totalWays %= mod;
    }
    
    long long int ans = (totalWays - invalidWays + mod) % mod;
    
    return ans;
}

```
