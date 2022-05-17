## Problem

#### [剑指 Offer 66. 构建乘积数组](https://leetcode.cn/problems/gou-jian-cheng-ji-shu-zu-lcof/)

给定一个数组 `A[0,1,…,n-1]`，请构建一个数组 `B[0,1,…,n-1]`，其中 `B[i]` 的值是数组 `A` 中除了下标 `i` 以外的元素的积, 即 `B[i]=A[0]×A[1]×…×A[i-1]×A[i+1]×…×A[n-1]`。不能使用除法。

 

------

### Note

- 前缀和思路

  

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
    vector<int> constructArr(vector<int>& a) {
        vector<int> res(a.size());
        int pre = 1;
        for(int i = 0; i < a.size(); ++i)
        {
            res[i] = pre;
            pre *= a[i];
        }

        pre = 1;
        for(int i = a.size() - 1; i >= 0; --i)
        {
            res[i] *= pre;
            pre *= a[i];
        }
        return res;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
