## Problem

#### [剑指 Offer 15. 二进制中1的个数](https://leetcode.cn/problems/er-jin-zhi-zhong-1de-ge-shu-lcof/)

编写一个函数，输入是一个无符号整数（以二进制串的形式），返回其二进制表达式中数字位数为 '1' 的个数（也被称为 [汉明重量](http://en.wikipedia.org/wiki/Hamming_weight)).）。

 

------

### Note

- 

------

### Complexity

- 时间O：二进制中1的位数
- 空间O：1

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int res = 0;
        while(n)
        {
            ++res;
            n &= (n - 1);
        }
        return res;        
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
