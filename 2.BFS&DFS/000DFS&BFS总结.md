## DFS&BFS总结

- 所谓的DFS,BFS就是一种遍历所有可能性的方法而已，与树的遍历没有什么不同。
  - 只不过二叉树的每个节点只有两种可能性，而DFS， BFS中的节点可能有数种选择的可能。



------

## DFS

典型程序：

[200. 岛屿数量](https://leetcode-cn.com/problems/number-of-islands/)

**掌握了这个程序，也就掌握了这类题目的核心。其他的各种变形，只是需要在此基础上加上逻辑即可。不要被迷惑！！！**

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

- [130. 被围绕的区域](https://leetcode-cn.com/problems/surrounded-regions/)  从边界出发。

- 岛屿周长[LeetCode 463. Island Perimeter](https://leetcode-cn.com/problems/island-perimeter/) （Easy） ：出了陆地的界（1.从1到0， 2.从1到grid边界外），说明出了边界，边界数+1

- 岛屿最大面积[LeetCode 695. Max Area of Island](https://leetcode-cn.com/problems/max-area-of-island/) （Medium）：没什么好说的。

- :heart: 填海造陆[LeetCode 827. Making A Large Island](https://leetcode-cn.com/problems/making-a-large-island/) （Hard）这已经是比较难的了

  - ```c++
        // 思路非常简单：
        // 第一次遍历：给现有的岛屿编号，并记录每个岛屿的面积
        // 第二次遍历：将所有grid[i][j] == 0 尝试分别设置为岛屿，然后看看四周是否有岛屿连接上
    ```

- [剑指 Offer 13. 机器人的运动范围](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/) 

- [733. 图像渲染](https://leetcode-cn.com/problems/flood-fill/)


## BFS

BFS其实和树的层序遍历是一个道理。 通常利用**队列**实现广度优先遍历。

很多时候对于遍历类题目：**使用DFS，比使用BFS的程序更加简洁。**

但是最短路径类的题目，还是只能用BFS.

- [Shortest Cycle Containing Target Node](https://binarysearch.com/problems/Shortest-Cycle-Containing-Target-Node)
- :heart:多源BFS [1162. 地图分析](https://leetcode-cn.com/problems/as-far-from-land-as-possible/)





