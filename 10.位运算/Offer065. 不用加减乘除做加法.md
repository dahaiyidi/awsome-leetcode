## Problem

#### [剑指 Offer 65. 不用加减乘除做加法](https://leetcode.cn/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)

写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号。

 

------

### Note

- 

------

### Complexity

- 时间O：
- 空间O：1

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    int add(int a, int b) {
        while(b)  // 直到进位为0
        {
            int c = ((unsigned int) (a & b)) << 1; // 只考虑进位  //C++中负数不支持左移位，因为结果是不定的
            a ^= b; // 不考虑进位
            b = c;
        }
        return a;
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
