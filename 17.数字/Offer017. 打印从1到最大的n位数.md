## Problem

#### [剑指 Offer 17. 打印从1到最大的n位数](https://leetcode.cn/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/)

输入数字 `n`，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。

**示例 1:**

```
输入: n = 1
输出: [1,2,3,4,5,6,7,8,9]
```

 

说明：

- 用返回一个整数列表来代替打印
- n 为正整数

------

### Note

- 大数问题
- 其实就是用回溯（dfs）解决排列组合问题


------

### Complexity

- 时间O：数字个数N
- 空间O：n

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    const string numbers{"0123456789"};
    vector<string> res;
    void inputNum(string s)
    {
        // 过滤不必要的0
        string tmp;
        bool starting = true; // 是否还需要判断string首部的0
        for(char c: s)
        {
            if(starting)
            {
                if(c == '0')
                {
                    // 0 跳过
                    continue;
                }
                else if(c != '0')
                {
                    starting = false; // 找到了不为0的数，则后续无序判断是否为0
                }
            }
            tmp += c;
        }
        if(tmp.compare("") != 0)
        // if(!tmp.empty())
        {
            // 不为"", 则可以加入
            res.push_back(tmp);
        }

    }
    void dfs(string& s, int pos)
    {
        if(pos == s.size())
        {
            inputNum(s);
            return;
        }
        for(int i = 0; i <= 9; ++i)
        {
            s[pos] = numbers[i];
            dfs(s, pos + 1);
        }
    }
    vector<int> printNumbers(int n) {
        // 本题目的本质是考察大数问题
        // 其实类似于回溯的题目，思路非常简单，就是从第一位开始dfs到n位数字，每个数字有0-9可以选择。
        // 只不过在push_back结果时，需要取出首部的0，而且00..00不能加入res
        string s(n, '0');
        dfs(s, 0);
        // 为了保证题目通过。。。
        vector<int> res2;
        for(string str: res)
        {
            res2.push_back(stoi(str));
        }
        return res2;        
    }

};
```



点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
