# 1218-LongestArithmeticSubsequence

LAS

https://leetcode-cn.com/problems/longest-arithmetic-subsequence-of-given-difference/

# 思路：

* 首先以动态规划题思考：找到： 
  * 状态  (state)
  * 转移（manually move the state)
  * 方程  (move by equation)
* 动态规划 O(n^2) 时间超时，根据等差数列的单调性（贪心思想?) 以越往后元素结尾的LAS 一定比前面差。所以可以 early return
* 根据 early return，也就是我们可以根据哈希表优化！


<img src="https://raw.githubusercontent.com/q815101630/pic_storage/main/img/image-20211106141135982.png" alt="image-20211106141135982" style="zoom:50%;" />

```python
class Solution:
    def longestSubsequence(self, arr: List[int], difference: int) -> int:
        ht = collections.defaultdict(int)
        for i in arr:
            ht[i] = ht[i-difference]+1
        return max(ht.values())
```

# 复杂度

时间 O(n)

空间 O(n)
