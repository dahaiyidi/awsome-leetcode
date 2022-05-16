## Problem

#### [剑指 Offer 56 - I. 数组中数字出现的次数](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

一个整型数组 `nums` 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

------

### Note

- 见code

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
    vector<int> singleNumbers(vector<int>& nums) {
        // 当只有一个数字不同时我们能够轻易的通过^得到结果
        // 先来一遍^ ，得到的结果k是两个目标数字（a和b）的抑或结果，我们想：如果能将nums分成两组，且a和b在不同的组就好了
        // 怎么分组？我们找到k的某位为1，根据改位上是否为1，可以将nums分成我们想要的两组！然后分别进行^
        vector<int> res;
        int k = 0;
        for(auto n : nums)
        {
            k ^= n;
        }

        int div = 1;
        while((k & div) == 0)
        {
            div <<= 1;
        }

        int a = 0;
        int b = 0;
        for(auto n: nums)
        {
            if((n & div) == 0)
            {
                a ^= n;
            }
            else
            {
                b ^= n;
            }
        }
        
        return {a, b};
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
