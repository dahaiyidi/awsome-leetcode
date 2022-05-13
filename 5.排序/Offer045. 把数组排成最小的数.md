## Problem

#### [剑指 Offer 45. 把数组排成最小的数](https://leetcode.cn/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

++

输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。

 

**示例 1:**f

```
输入: [10,2]
输出: "102"
```

**示例 2:**

```
输入: [3,30,34,5,9]
输出: "3033459"
```

 

------

### Note

- 思路不难
- 考察自定义排序规则

------

### Complexity

- 时间O：nlogn
- 空间O：n

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    string minNumber(vector<int>& nums) {
        vector<string> strs;
        for(auto n : nums)
        {
            strs.push_back(to_string(n));
        }
        sort(strs.begin(), strs.end(), [] (string& x, string& y){
            return x + y < y + x;
        });  // 此处是比较的关键
        string res;
        for(auto str: strs)
        {
            res += str;
        }
        return res;

    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
