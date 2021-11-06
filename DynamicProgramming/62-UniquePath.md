# 62-UniquePath

https://leetcode-cn.com/problems/unique-paths/

# 思路

经典题目，直接看note

![image-20211106154124280](https://raw.githubusercontent.com/q815101630/pic_storage/main/img/image-20211106154124280.png)



```python
# 没压缩
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        row1 = [1]*n
        row2 = [0]*n
        row2[0] = 1

        for i in range(m):
            dp[i][0] = 1
        for j in range(n):
            dp[0][j] = 1
        
        for i in range(1, m):
            for j in range(1, n):
                dp[i][j] = dp[i-1][j] + dp[i][j-1]
        
        return dp[-1][-1]
# 压缩
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        row1 = [1]*n
        row2 = [1]*n

        for i in range(1, m):
            for j in range(1, n):
                row2[j] = row1[j] + row2[j-1]
            # row2 moves up and recycle row1
            row1 = row2
            row2 = row1
        return row2[-1]
```



# 复杂度

状压前：

时空O(m*n)

状压后：

时间O(m*n)

空间O(n)