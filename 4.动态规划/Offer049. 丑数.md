## Problem

#### [剑指 Offer 49. 丑数](https://leetcode.cn/problems/chou-shu-lcof/)

中等++

我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。

 

------

### Note

- a,b,c代表下一个2需要×的数字的索引
- 每次从待选中选择一个较小的数字后，将相应的a或b或c加1
- 更像是三指针

------

### Complexity

- 时间O：n
- 空间O：n

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    int nthUglyNumber(int n) {
        int dp[n];
        dp[0] = 1;
        int a = 0; // 指向需要*2的索引
        int b = 0; // 指向需要*3的索引
        int c = 0; // 指向需要*4的索引
        for(int i = 1; i < n; ++i)
        {
            int n2 = dp[a] * 2;
            int n3 = dp[b] * 3;
            int n5 = dp[c] * 5;

            // 获取3个待选的最小值作为dp[i]
            dp[i] = min(min(n2, n3), n5);

            if(dp[i] == n2)  ++a;
            if(dp[i] == n3)  ++b;
            if(dp[i] == n5)  ++c;
        }
        return dp[n - 1];

    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
