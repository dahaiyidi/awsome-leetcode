## Problem

#### [剑指 Offer 64. 求1+2+…+n](https://leetcode.cn/problems/qiu-12n-lcof/)

求 `1+2+...+n` ，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。

------

### Note

- 知道使用递归，但是如何通过不使用if，指定终止条件。

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
    int sumNums(int n) {
        // 通过 && 巧妙地进行终止判断
        n && (n += sumNums(n - 1));
        return n; 
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
