## Problem

#### [剑指 Offer 57. 和为s的两个数字](https://leetcode.cn/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

------

### Note

- 思路不难
- 典型双指针

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
    vector<int> twoSum(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size() - 1;
        while(left < right)
        {
            int tmp = nums[left] + nums[right];
            if(tmp < target)
            {
                ++left;
            }
            else if(tmp > target)
            {
                --right;
            }
            else if(tmp == target)
            {
                return {nums[left], nums[right]};
            }

        }
        return {};

    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
