## Problem

#### [剑指 Offer 57 - II. 和为s的连续正数序列](https://leetcode.cn/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

输入一个正整数 `target` ，输出所有和为 `target` 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

**示例 1：**

```
输入：target = 9
输出：[[2,3,4],[4,5]]
```

**示例 2：**

```
输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
```

------

### Note

- 见code
- **表示滑动窗口的双指针**

------

### Complexity

- 时间O：n
- 空间O：1

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    vector<vector<int>> findContinuousSequence(int target) {
        vector<vector<int>> res;

        int i = 1;
        int j = 2;
        int sum = 3;
        while(i < j)
        {
            if(sum == target)
            {
                vector<int> tmp;
                for(int k = i; k <= j; ++k)
                {
                    tmp.push_back(k);
                }
                res.push_back(tmp);
                sum -= i;
                ++i;
            }
            else if(sum > target)
            {
                sum -= i;
                ++i;
            }
            else if(sum < target)
            {
                ++j;
                sum += j;
            }
        }
        return res;
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
