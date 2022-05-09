## Problem

#### [剑指 Offer 46. 把数字翻译成字符串](https://leetcode-cn.com/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/)

简单++

给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。

同[91. 解码方法](https://leetcode-cn.com/problems/decode-ways/)

------

### Note

- 思路不难
- 常规动规，只是逻辑上需要想一下。

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
    int translateNum(int num) {
        if(num < 10) return 1;
        string nums = to_string(num);
        int a = 1;
        int b = 1;
        int c = 0;
        for(int i = 1; i < nums.size(); ++i)
        {
            string tmp = nums.substr(i - 1, 2);
            if(tmp >= "10" && tmp <= "25")
            {
                c = a + b;
            }
            else
            {
                c = b;
            }
            a = b;
            b = c;
        }
        return c;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
