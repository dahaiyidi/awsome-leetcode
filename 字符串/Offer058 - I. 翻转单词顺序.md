## Problem

#### [剑指 Offer 58 - I. 翻转单词顺序](https://leetcode.cn/problems/fan-zhuan-dan-ci-shun-xu-lcof/)

输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。为简单起见，标点符号和普通字母一样处理。例如输入字符串"I am a student. "，则输出"student. a am I"。

 

**示例 1：**

```
输入: "the sky is blue"
输出: "blue is sky the"
```

**示例 2：**

------

### Note

- 可以使用istringstream 简化流程

------

### Complexity

- 时间O：n
- 空间O：n

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    string reverseWords(string s) {
        
        istringstream input(s);
        stack<string> st;
        string res;
        string str;
        while(input >> str)
        {
            st.push(str);
            cout << str << endl;
        }
        while(!st.empty())
        {
            res += (st.top() + " ");
            st.pop();           
        }
        res.pop_back();

        return res;
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
