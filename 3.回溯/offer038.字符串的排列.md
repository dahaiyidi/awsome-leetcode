## Problem

#### [剑指 Offer 38. 字符串的排列](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)

输入一个字符串，打印出该字符串中字符的所有排列。

 

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

 

**示例:**

```
输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
```

 

------

### Note

- 思路同[47. 全排列 II](https://leetcode-cn.com/problems/permutations-ii/)
- 不要因为是字符串就不敢下手。

------

### Complexity

- 时间O：
- 空间O：

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    void dfs(string& goods, vector<string>& res, vector<char>& path, vector<bool>& used)
    {
        if(path.size() == goods.size())
        {
            string temp(path.begin(), path.end());
            res.emplace_back(temp);
            return;
        }
        for(int i = 0; i < goods.size(); i++)
        {
            if(used[i] || (i > 0 && goods[i] == goods[i-1] && !used[i-1]))
            {
                continue;
            }
            path.push_back(goods[i]);
            used[i] = true;
            dfs(goods, res, path, used);
            used[i] = false;
            path.pop_back();
        }
    }

    vector<string> goodsOrder(string goods) {
        vector<string> res;
        vector<char> path;
        vector<bool> used(goods.size(), false);
        sort(goods.begin(), goods.end());
        dfs(goods, res, path, used);
        return res;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
