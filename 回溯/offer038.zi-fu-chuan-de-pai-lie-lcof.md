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
    void dfs(string& s, int depth, vector<bool>& used, vector<string>& res, vector<char>& path){
        if(depth == s.size()){
            string temp(path.begin(), path.end());
            res.emplace_back(temp);
        }

        for(int i = 0; i < s.size(); i++){
            if(used[i] || (i > 0 && s[i] == s[i - 1] && !used[i - 1])){
                continue;
            }
            path.emplace_back(s[i]);
            used[i] = true;

            dfs(s, depth + 1, used, res, path);

            path.pop_back();
            used[i] = false;
        }

    }
    vector<string> permutation(string s) {
        vector<string> res;
        vector<char> path;
        vector<bool> used(s.size(), false);
        sort(s.begin(), s.end());
        dfs(s, 0, used, res, path);
        return res;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
