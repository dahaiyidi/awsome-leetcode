## Problem

#### [剑指 Offer 53 - II. 0～n-1中缺失的数字](https://leetcode.cn/problems/que-shi-de-shu-zi-lcof/)

一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。

 

**示例 1:**

```
输入: [0,1,3]
输出: 2
```

**示例 2:**

```
输入: [0,1,2,3,4,5,6,7,9]
输出: 8
```

 

------

### Note

- 普通二分，只不过题目不同而已

------

### Complexity

- 时间O：logn
- 空间O：1

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int left = 0;
        int right = nums.size() - 1;
        while(left <= right)
        {
            int mid = left + ((right - left) >> 1);
            // 肯定有nums[i] >= i
            if(nums[mid] > mid)
            {
                right = mid - 1;
            }
            else if(nums[mid] == mid)
            {
                left = mid + 1;
            }
            
        }
        // 经过分析发现，最终退出时left就位于缺失的位置上
        return left;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
