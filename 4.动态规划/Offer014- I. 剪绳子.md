## Problem

#### [剑指 Offer 14- I. 剪绳子](https://leetcode-cn.com/problems/jian-sheng-zi-lcof/)

中等

给你一根长度为 `n` 的绳子，请把绳子剪成整数长度的 `m` 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 `k[0],k[1]...k[m-1]` 。请问 `k[0]*k[1]*...*k[m-1]` 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

本题与主站 343 题相同：https://leetcode-cn.com/problems/integer-break/

------

### Note

- 思路1：数学方法
  - 获得尽量多的3
  - 当最终剩余1，2， 3，4， 则直接停止，因为他们不需要再分，越分约小。

- 思路2：动态规划

#### [剑指 Offer 14- II. 剪绳子 II](https://leetcode-cn.com/problems/jian-sheng-zi-ii-lcof/)要求 答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。可以这样修改：

```c++
class Solution {
public:
    int cuttingRope(int n) {
        if(n < 4)
        {
            return n - 1; // 因为必须要截断
        }
        long res = 1;
        while(n > 4)
        {
            //res = res * 3 % 1000000007;
            n -= 3;
        }
        return n * res % 1000000007;

    }
};
```



------

### Complexity

- 时间O：
- 空间O：

------

### Python

```python

```

### C++

```C++
数学方法
class Solution {
public:
    int cuttingRope(int n) {
        // 是一个数学题目。。。
        // 最好是所有段均相等
        // 通过求导，可知当长度都为3时最终的乘积会最大
        if(n <= 3) return n - 1; // 必须要切一刀
        int a = n / 3;
        int b = n % 3;
        int res = 0;
        if(b == 0)
        {
            res = pow(3, a);
        }
        else if(b == 1)
        {
            res = pow(3, a - 1) * 4;
        }
        else if(b == 2)
        {
            res = pow(3, a) * 2;
        }
        return res;
    }
};

动态规划
class Solution {
public:
    int cuttingRope(int n) {
        // dp[i] 代表长度为i的最优值
        // 对于所有的j [1, i - 1], 取当第一段的长度为j时，整体成绩最大值为max(j * (i - j), j * dp[i - j])， 取所有j对应值的最大值
        // 此处将第一段长度设置为j，可以将问题的表达式方便的写出来。 将不确定的东西转化为确定的东西。
        vector<int> dp(n + 1, 0);
        dp[2] = 1;
        for(int i = 3; i <= n; ++i)
        {
            for(int j = 1; j <= i - 2; ++j)
            {
                dp[i] = max(dp[i], max(j * (i - j), j * dp[i - j]));
            }
        }
        return dp[n];
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
