## Problem

#### [剑指 Offer 03. 数组中重复的数字](https://leetcode.cn/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

简单++

找出数组中重复的数字。



 在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

------

### Note

- 思路值得借鉴：如何有效利用**在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内**
- 建议也查看[287. 寻找重复数](https://leetcode-cn.com/problems/find-the-duplicate-number/)  利用链表中环的概念解决，**思考如何利用值与索引范围相同**
- [448. 找到所有数组中消失的数字](https://leetcode.cn/problems/find-all-numbers-disappeared-in-an-array/)

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
    int findRepeatNumber(vector<int>& nums) {
        //  https://leetcode.cn/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/solution/yuan-di-jiao-huan-yi-jiao-huan-luo-bu-bi-gh5c/
        for(int i = 0; i < nums.size(); ++i)
        {
            while(i != nums[i]) // 发现这个坑里的萝卜不是自己家的
            {
                int val = nums[i];

                // 重复:看看你家里有没有和你一样的萝卜
                if(nums[val] == nums[i]) 
                {
                    return nums[i];
                }

                // 把val送到合适的位置，然后继续判断交换来的值
                // 把你送回你家去，然后把你家里的那个萝卜拿回来,然后继续判断拿回来的萝卜
                swap(nums[i], nums[val]);
            }
        }
        return -1;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
