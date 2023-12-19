## Problem

#### [剑指 Offer 61. 扑克牌中的顺子](https://leetcode.cn/problems/bu-ke-pai-zhong-de-shun-zi-lcof/)

简单++

从**若干副扑克牌**中随机抽 `5` 张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14。

 

**示例 1:**

```
输入: [1,2,3,4,5]
输出: True
```

 

**示例 2:**

```
输入: [0,0,1,2,5]
输出: True
```

 

------

### Note

- 思路不难
- **需要排除重复元素的情况，则需要排序**
- 设0的个数为count
- 排序后，除0之外的最大值与最小值的插值<=4， 且不能有重复数字

------

### Complexity

- 时间O：nlogn
- 空间O：logn  排序使用的空间。

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    bool isStraight(vector<int>& nums) {
        int count = 0;        
        sort(nums.begin(), nums.end());
        for(int i = 0; i < nums.size() - 1; ++i)
        {
            if(nums[i] == 0)  
            {
                ++count;
                continue;
            }
            if(nums[i] == nums[i + 1]) return false;
        }
        return nums[4] - nums[count] <= 4; // 即便全是0也没有问题
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
