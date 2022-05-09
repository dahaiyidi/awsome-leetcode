## Problem

#### [剑指 Offer 60. n个骰子的点数](https://leetcode.cn/problems/nge-tou-zi-de-dian-shu-lcof/)

中等++

把n个骰子扔在地上，所有骰子朝上一面的点数之和为s。输入n，打印出s的所有可能的值出现的概率。 

你需要用一个浮点数数组返回答案，其中第 i 个元素代表这 n 个骰子所能掷出的点数集合中第 i 小的那个的概率。

 

------

### Note

- 思路见code
- **本质上该题目就是不停地递归地将概率均匀的分成6份**
- 这些题目的规律不太好看出来：[剑指 Offer 49. 丑数](https://leetcode.cn/problems/chou-shu-lcof/)
- 概率型问题：[688. 骑士在棋盘上的概率](https://leetcode-cn.com/problems/knight-probability-in-chessboard/)

------

### Complexity

- 时间O：n^2
- 空间O：n

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    vector<double> dicesProbability(int n) {
        // 本质上该题目就是不停地递归地将概率均匀的分成6份
        // dp[i][j]表示的是前i个骰子的点数之和为j的概率
        // 由于dp[i]只与dp[i - 1]有关系，则可以优化空间复杂度为线性复杂度
        // 骰子编号从1开始
        vector<double> dp(6, 1.0 / 6.0);  // 0号骰子只有6种情况。
        for(int i = 2; i <= n; ++i)
        {
            // 求第i骰子时的情况
            // 取值范围为i~6i, 长度为5 * i + 1
            // 第i骰子的取值范围是1~6，因此对于前i-1个骰子的情况的一个值 dp[j] 可以变为 dp[j] + 1 ~ dp[j] + 6， 因此将dp[j]的概率平均分到 dp[j] + 1 ~ dp[j] + 6即可。
            vector<double> tmp(5 * i + 1, 0);
            for(int j = 0; j < dp.size(); ++j)
            {
                for(int k = 0; k < 6; ++k)
                {
                    tmp[j + k] += dp[j] / 6.0; // 将dp[j]分成6份到tmp[j + 1] ~ tmp[j + 6]
                }
            }
            // 至此，0~i号骰子的结果更新完毕
            dp = tmp; 

        }
        return dp;

    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
