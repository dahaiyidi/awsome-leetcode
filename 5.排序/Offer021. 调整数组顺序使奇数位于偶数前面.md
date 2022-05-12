## Problem

#### [剑指 Offer 21. 调整数组顺序使奇数位于偶数前面](https://leetcode.cn/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。

 

**示例：**

```
输入：nums = [1,2,3,4]
输出：[1,3,2,4] 
注：[3,1,2,4] 也是正确的答案之一。
```

 

------

### Note

- 双指针

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
    vector<int> exchange(vector<int>& nums) {
        int i = 0;
        int j = 0;
        for(j = 0; j < nums.size(); ++j)
        {
            if((nums[j] & 1) == 1)
            {
                // nums[j] 为奇数
                swap(nums[i++], nums[j]);
                // 或者：
                // if(i != j) swap(nums[i], nums[j]);
                // ++i;
            }

        }
        return nums;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
