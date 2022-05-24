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
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        if(matrix.empty() || matrix[0].empty())
        {
            return {};
        }
        vector<int> res;
        int m = matrix.size();
        int n = matrix[0].size();
        int i = 0;
        int j = 0;

        for(int k = 0; k <= (n - 1) / 2 && k <= (m - 1) / 2; ++k)
        {
            i = k;
            for(j = k; j <= n - 1 - k; ++j)
            {
                // cout << 11 << endl;
                res.push_back(matrix[i][j]);
            }

            j = n - 1 - k;
            for(i = k + 1; i <= m - 1 - k; ++i)
            {
                //cout << 22 << endl;
                res.push_back(matrix[i][j]);
            }

            i = m - 1 - k;
            for(j = n - 1 - k - 1; j >= k && i > k; --j)   // 记得添加条件  i > k
            {
                //cout << 33 << endl;
                res.push_back(matrix[i][j]);
            }

            j = k;
            for(i = m - 1 - k - 1; i >= k + 1 && n - 1 - k >k; --i)  // 记得添加条件  n - 1 - k >k
            {
                //cout << 44 << endl;
                res.push_back(matrix[i][j]);
            }   

        }
        return res;

    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
