## Problem

#### [剑指 Offer 42. 连续子数组的最大和](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

简单

输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。 

------

### Note

- 状态：dp[i]为以sales[i]为最后一天的最优值
- 转移：dp[i] = max(nums[i], dp[i - 1] + nums[i])
- 空间可以优化为常数空间

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
    int maxSubArray(vector<int>& nums) {
        // d[i]
        // vector<int> dp(nums.size());
        int res = nums[0];
        int a = nums[0];
        int b;
        for(int i = 1; i < nums.size(); ++i)
        {
            b = max(nums[i], a + nums[i]);
            res = max(res, b);
            a = b;
        }
        return res;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
