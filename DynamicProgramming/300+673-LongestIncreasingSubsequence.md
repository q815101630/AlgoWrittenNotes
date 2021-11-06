# LongestIncreasingSubsequence

Leetcode 300 + 673

# 思路

673 是 lc300 的进阶。相较于lc300，这道题要求多存了一个信息，具体看note

![image-20211106141513631](https://raw.githubusercontent.com/q815101630/pic_storage/main/img/image-20211106141513631.png)

![image-20211106141522308](https://raw.githubusercontent.com/q815101630/pic_storage/main/img/image-20211106141522308.png)

```python
#lc300
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = [1 for i in nums]
        for i in range(1, len(nums)):
            for j in range(i-1, -1, -1):
                if nums[i] > nums[j]:
                    dp[i] = max(dp[i], dp[j]+1)

        theLongest = max(dp, key= lambda x: x[0])
        for i in range(len(dp)-1, -1, 0):
            if theLongest == dp[i][0]:
                return dp[i][1]
```

```python
# lc600
class Solution:
    def findNumberOfLIS(self, nums: List[int]) -> int:
        dp = [[1,1] for i in nums]
        for i in range(1, len(nums)):
            for j in range(i-1, -1, -1):
                if nums[i] > nums[j]:
                    if dp[j][0]+1 > dp[i][0]:
                        dp[i][0] = dp[j][0]+1
                        dp[i][1] = dp[j][1]
                    elif dp[j][0] + 1 == dp[i][0]:
                        dp[i][1] += dp[j][1]
            
        theLongest = max(dp, key= lambda x: x[0])
        output = 0
        for i,v in dp:
            if theLongest[0] == i:
                output += v
        return output    
```

# 复杂度

时空显而易见都是O(n^2)