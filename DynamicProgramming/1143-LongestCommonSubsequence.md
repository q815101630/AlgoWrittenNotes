# 1143-LongestCommonSubsequence

LCS

https://leetcode-cn.com/problems/longest-common-subsequence/

# 思路

* 动态规划
* 一般得我们用两个 arr 的end index 作为决定转移状态的关键值
* 看note

![image-20211106151128463](https://raw.githubusercontent.com/q815101630/pic_storage/main/img/image-20211106151128463.png)

```python
class Solution:
    def longestCommonSubsequence(self, text1: str, text2: str) -> int:
        dp = [[0]*(len(text2)+1) for _ in range(len(text1)+1)]

        for i in range(1, len(text1)+1):
            for j in range(1, len(text2)+1):
                if text1[i-1] == text2[j-1]:
                    dp[i][j] = dp[i-1][j-1]+1
                else:
                    dp[i][j] = max(dp[i][j-1], dp[i-1][j])
        return dp[-1][-1]
```

# 复杂度

时空O(n^2)