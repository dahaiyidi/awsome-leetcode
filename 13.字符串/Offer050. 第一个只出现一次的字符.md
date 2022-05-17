## Problem

#### [剑指 Offer 50. 第一个只出现一次的字符](https://leetcode.cn/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

------

### Note

- 无聊的题目

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
    char firstUniqChar(string s) {
        vector<int> count(26);
        // 使用unordered_map 也可以
        for(auto c: s)
        {
            ++count[c - 'a'];
        }
        for(auto c: s)
        {
            if(count[c - 'a'] == 1)
            {
                return c;
            }
        }
        return ' ';
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
