## Problem

#### [剑指 Offer 12. 矩阵中的路径](https://leetcode.cn/problems/ju-zhen-zhong-de-lu-jing-lcof/)

给定一个 `m x n` 二维字符网格 `board` 和一个字符串单词 `word` 。如果 `word` 存在于网格中，返回 `true` ；否则，返回 `false` 。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

例如，在下面的 3×4 的矩阵中包含单词 "ABCCED"（单词中的字母已标出）。

同[79. 单词搜索](https://leetcode.cn/problems/word-search/)

------

### Note

- 标准回溯

------

### Complexity

- 时间O：`M*N*3^L`, L 为string长度
- 空间O：M*N

------

### Python

```python

```

### C++

```C++
class Solution {
    const int dx[4] = {0, 0, 1, -1};
    const int dy[4] = {1, -1, 0, 0};
public:
    bool dfs(vector<vector<char>>& board, vector<vector<bool>>& visited, string& word, int i , int j, int n)
    {
        if(n == word.size())
        {
            return true;
        }

        if(i < 0 || i >= board.size() || j < 0 || j >= board[0].size() || visited[i][j] || board[i][j] != word[n])
        {
            return false;
        }

        visited[i][j] = true;
        for(int k = 0; k < 4; ++k)
        {
            // 也可以直接在此处过滤ij坐标
            if(dfs(board, visited, word, i + dx[k], j + dy[k], n + 1))
            {
                return true;
            }
        }
        visited[i][j] = false;
        return false;
    }
    bool exist(vector<vector<char>>& board, string word) {
        int m = board.size();
        int n = board[0].size();
        vector<vector<bool>> visited(m, vector<bool> (n, false) );
        for(int i = 0; i < m; ++i)
        {
            for(int j = 0; j < n; ++j)
            {
                if(dfs(board, visited, word, i, j, 0))
                {
                    return true;
                }                
            }
        }
        return false;
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
