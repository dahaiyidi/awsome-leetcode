## Problem

#### [剑指 Offer 39. 数组中出现次数超过一半的数字](https://leetcode.cn/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

简单++

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。



你可以假设数组是非空的，并且给定的数组总是存在多数元素。

同[169. 多数元素](https://leetcode.cn/problems/majority-element/)

------

### Note

- 好好看一下思路。

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

    int majorityElement(vector<int>& nums) {
        int x = 0; 
        int count = 0;
        for(auto n : nums)
        {
            if(count == 0)
            {
                // 重新开始
                x = n;
                count = 1;
            }
            else if(count > 0)
            {
                count += (n == x ? 1: -1);
            }
        }
        return x;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
