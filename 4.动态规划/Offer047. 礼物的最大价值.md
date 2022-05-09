## Problem

#### [剑指 Offer 47. 礼物的最大价值](https://leetcode.cn/problems/li-wu-de-zui-da-jie-zhi-lcof/)

在一个 m*n 的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值（价值大于 0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向右或者向下移动一格、直到到达棋盘的右下角。给定一个棋盘及其上面的礼物的价值，请计算你最多能拿到多少价值的礼物？

 

------

### Note

- 标准的普通动规问题
- 状态：`dp[i][j]为运动到该位置的最优值`
- 转移：`dp[i][j] = grid[i][j] + max(dp[i-1][j], dp[i][j-1])`
- 空间可以优化为n

------

### Complexity

- 时间O：m*n
- 空间O：n

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    int maxValue(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        vector<int> dp(n);
        dp[0] = grid[0][0];
        // 初始化第一行
        for(int j = 1; j < n; ++j)
        {
            dp[j] = grid[0][j] + dp[j - 1];
        }
        // 开始往下递推
        for(int i = 1; i < m; ++i)
        {
            dp[0] += grid[i][0]; // 计算该行的第一个元素
            for(int j = 1; j < n ; ++j)
            {
                dp[j] = grid[i][j] + max(dp[j - 1], dp[j]);
            }
        }
        return dp[n - 1];
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
