## Problem

#### [剑指 Offer 13. 机器人的运动范围](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/)

中等++

地上有一个m行n列的方格，从坐标 `[0,0]` 到坐标 `[m-1,n-1]` 。一个机器人从坐标 `[0, 0] `的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

------

### Note

- 这道题目真正验证了：最大的敌人就是自己。自己已经把自己吓倒了。
- 其实就是简单的DFS或BFS。而dfs与bfs本质上就是树的递归版遍历和层序遍历。

------

### Complexity

- 时间O：MN
- 空间O：MN

------

### Python·

```python

```

### C++

```C++
class Solution {
public:
    int m;
    int n;
    int k;
    int dfs(int i, int j, int si, int sj, vector<vector<bool>>& visited)
    {
        if(i >= m || j >= n || si + sj > k || visited[i][j])
        {
            return 0;
        }
        visited[i][j] = true;
        int tmp1 = dfs(i + 1, j, (i + 1) % 10 == 0? si -8: si + 1, sj, visited);
        int tmp2 = dfs(i , j + 1, si, (j + 1) % 10 == 0? sj - 8: sj + 1, visited);
        return 1 + tmp1 + tmp2;  // 与树非常相像
    }
    int movingCount(int m, int n, int k) {
        // BFS, DFS都可以，反正都是遍历而已

        this->m = m;
        this->n = n;
        this->k = k;
        vector<vector<bool>> visited(m, vector<bool>(n, false));
        int res = dfs(0, 0, 0, 0, visited);
        return res;
    }
};



///////2
class Solution {
public:
    int wardrobeFinishing(int m, int n, int cnt) {
        vector<vector<bool>> visited(m, vector<bool>(n, false));
        int res = dfs(0, 0, 0, 0, visited, cnt);
        return res;       

    }

    int dfs(int i , int j, int si, int sj, vector<vector<bool>>& visited, const int cnt)
    {
        if(i < 0 || i>= visited.size() || j < 0  || si + sj > cnt|| j >=visited[0].size() || visited[i][j])
            return 0;
        visited[i][j] = true;
        
        int val_1 = dfs(i + 1, j, (i + 1)%10 ==0? si -8:si +1, sj, visited, cnt);
        int val_2 = dfs(i, j + 1, si, (j + 1)%10 ==0? sj -8:sj +1, visited, cnt);
        return 1 + val_1 + val_2;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
