## Problem

#### [剑指 Offer 56 - II. 数组中数字出现的次数 II](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

在一个数组 `nums` 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字。

 

------

### Note

- https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/

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
    int singleNumber(vector<int>& nums) {
        // 在推导ones = ones ^ n & ~twos;问题不大
        // 但是怎么推导twos = twos ^ n & ~ones;呢？
        // 首先根据ones = ones ^ n & ~twos;更新一步状态，在新的状态上交换两者的位置即可得到相同的状态转移方式。
        int ones = 0;
        int twos = 0;
        for(auto n : nums)
        {
            ones = ones ^ n & ~twos;
            twos = twos ^ n & ~ones;
        }
        return ones;

    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
