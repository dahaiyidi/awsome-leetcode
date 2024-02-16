## Problem

#### [剑指 Offer 29. 顺时针打印矩阵](https://leetcode.cn/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)

输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

 

**示例 1：**

```
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
```

------

### Note

- 思路简单
- 只是不要忘记需要在第3段和第4段加上判断条件：起始位置要位于右半部（下半部）

------

### Complexity

- 时间O：m*n
- 空间O：1

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    vector<int> spiralArray(vector<vector<int>>& array) {
        if(array.size() == 0) return {};
        int m = array.size();
        int n = array[0].size();
        int u = 0, d= m -1, l=0, r = n-1;

        vector<int> res;

        while(true)
        {
            for(int col = l; col <= r; col++) res.push_back(array[u][col]);
            u++;
            if(u > d) break;

            for (int row = u; row <= d; row++) res.push_back(array[row][r]);
            r--;
            if(r < l) break;

            for (int col = r; col >= l; col--) res.push_back(array[d][col]);
            d--;
            if(d < u) break;

            for (int row = d; row >= u; row--) res.push_back(array[row][l]);
            l++;
            if(l > r) break;
        }
        return res;       

    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
