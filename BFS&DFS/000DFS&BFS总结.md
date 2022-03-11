## DFS&BFS总结

岛屿周长[LeetCode 463. Island Perimeter](https://leetcode-cn.com/problems/island-perimeter/) （Easy）

岛屿最大面积[LeetCode 695. Max Area of Island](https://leetcode-cn.com/problems/max-area-of-island/) （Medium）

填海造陆[LeetCode 827. Making A Large Island](https://leetcode-cn.com/problems/making-a-large-island/) （Hard）

------

### 

典型程序：

[200. 岛屿数量](https://leetcode-cn.com/problems/number-of-islands/)

```c++
class Solution {
public:
    int num = 0;
    void dfs(vector<vector<char>>& grid, int i, int j){
        if(i < 0 || i >= grid.size() || j < 0 || j >=grid[0].size() || grid[i][j] != '1'){
            return;
        }        
        grid[i][j] = '2';
        dfs(grid, i + 1, j);
        dfs(grid, i - 1, j);
        dfs(grid, i, j + 1);
        dfs(grid, i, j - 1);
    }
    int numIslands(vector<vector<char>>& grid) {
        int res = 0;
        for(int i = 0; i < grid.size(); i++){
            for(int j = 0; j < grid[0].size(); j++){
                if(grid[i][j] == '1'){
                    res++;
                    dfs(grid, i, j);
                }
            }
        }
        return res;

    }
};
```

