# 688-KnightProbabilityinChessboard

#### [Knight Probability in Chessboard](https://leetcode-cn.com/problems/knight-probability-in-chessboard/)



首先自己尝试backtrack解题，但是发现对于概率不熟悉。重点在于把整个棋盘每一步之后棋仍在棋盘上的所有概率考虑起来。具体看note

![image-20211106165609512](https://raw.githubusercontent.com/q815101630/pic_storage/main/img/image-20211106165609512.png)

```python
class Solution:
    def knightProbability(self, N: int, k: int, row: int, column: int) -> float:
        dir = ((2,1),(2,-1),(-2,1),(-2,-1),(1,2),(1,-2),(-1,2),(-1,-2))

        dp = [[0]*N for _ in range(N)]
        dp[row][column] = 1

        for step in range(k):
            temp = [[0]*N for _ in range(N)]
            for i in range(N):
                for j in range(N):
                    for di,dj in dir:
                        lastI, lastJ = i-di, j-dj
                        if 0<=lastI<N and 0<=lastJ<N:
                            temp[i][j] += dp[lastI][lastJ]/8
            
            dp = temp

        res = 0
        for i in dp:
            for j in i:
                res  += j
        
        return res
```

# 复杂度：

时间：O(kNN)

空间: O(NN)

