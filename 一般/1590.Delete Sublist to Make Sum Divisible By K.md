## Problem

#### [1590. 使数组和能被 P 整除](https://leetcode-cn.com/problems/make-sum-divisible-by-p/)

难度中等52

给你一个正整数数组 `nums`，请你移除 **最短** 子数组（可以为 **空**），使得剩余元素的 **和** 能被 `p` 整除。 **不允许** 将整个数组都移除。

请你返回你需要移除的最短子数组的长度，如果无法满足题目要求，返回 `-1` 。

**子数组** 定义为原数组中连续的一组元素。



------

### Note

- 转化为最段前缀和问题。
- mod = sum % p，则只需要**寻找最短子序列和%p后为mod即可**
- 在计算累加和时，curmod = cursum % p, 则需要寻找哪个前缀和%p后，为targetmod，计算方式如下：targetmod = curmod - mod； 如果curmod - mod<0 则还需要加上一个p，即targetmod = curmod - mod + p
- 最终还要去除将整个list删除的情况
- 关联问题：[974. 和可被 K 整除的子数组](https://leetcode-cn.com/problems/subarray-sums-divisible-by-k/)

------

### Complexity

- 时间O：n
- 空间O：n

------

### Python

```python
class Solution:
    def minSubarray(self, nums: List[int], p: int) -> int:
        sum = list(accumulate(nums, add))
        mod = sum[-1] % p
        if mod == 0:
            return 0
        hashtable = {0: -1}  # 如果targetmod=0， 则当前可行的长度为i + 1

        res = len(nums)
        for i in range(len(nums)):
            curmod = sum[i] % p
            hashtable[curmod] = i
            targetmod = curmod - mod
            if targetmod < 0:
                targetmod += p
            if targetmod in hashtable:
                res = min(res, i - hashtable[targetmod])
        
        # 避免将整个list删除
        if res == len(nums):
            res = -1
        return res

```

### C++

```C++
class Solution {
public:
    int minSubarray(vector<int>& nums, int p) {
        long long sum = 0;
        for(int n: nums){
            sum += (long long)n;
        }
        long long mod = sum % (long long)p;
        if(mod == 0ll){
            return 0;
        }
        int res = nums.size();
        unordered_map<long long, int> table;
        table[0ll] = -1; //如果targetmod=0， 则当前可行的长度为i + 1

        sum = 0;
        for(int i = 0; i < nums.size(); i++){
            sum += (long long)nums[i];
            long long curmod = sum % (long long)p;
            table[curmod] = i;

            long long targetmod = curmod - mod;
            if(curmod < mod){
                targetmod += p;
            }
            if (table.count(targetmod)){
                res = min(res, i - table[targetmod]);
            }
        }
        return res == nums.size() ? -1: res;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
