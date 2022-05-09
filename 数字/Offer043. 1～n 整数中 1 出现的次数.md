## Problem

#### [剑指 Offer 43. 1～n 整数中 1 出现的次数](https://leetcode.cn/problems/1nzheng-shu-zhong-1chu-xian-de-ci-shu-lcof/)

困难++

输入一个整数 `n` ，求1～n这n个整数的十进制表示中1出现的次数。

例如，输入12，1～12这些整数中包含1 的数字有1、10、11和12，1一共出现了5次。

------

### Note

-  想象 ： 一个密码锁 将 [0] 换成 [1] ，然后拨动其他位置，使得拨动后的数字不得超过 1 2 [0] 1 这样就可以统计出 [0] 处 1 出现的个数 ，以此类推 将 每位 1 出现次数 相加得到 结果

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
    int countDigitOne(int n) {
        // 想象 ： 一个密码锁 将 [0] 换成 [1] ，然后拨动其他位置，使得拨动后的数字不得超过 1 2 [0] 1 这样就可以统计出 [0] 处 1 出现的个数 ，以此类推 将 每位 1 出现次数 相加得到 结果
        // 当第i位(i 从右0开始)值为cur时， 如果考虑当前位为1的可能数量时， high 表示的是cur左边的字面值， low表示的是cur右边的字面值, 令digit = 10 ^ i
        // 当cur = 0,  左面的可以为0 ~ high - 1，共high个可能; 右面的可能的数值个数为10 ^ digit， 因此 high *  digit
        // 当cur = 1， 则在cur=0的基础上 增加了0~low, 也就是 + low + 1, 
        // 当cur > 1， 在cur=0的基础上， + digit
        int low = 0;
        int cur = n % 10;
        int high = n / 10;
        int res = 0;
        long long digit = 1;

        while(high != 0 || cur != 0)
        {
            // 此处digit直接相当于前面的(10 ^ digit)
            if(cur == 0) res += high * digit;
            else if(cur == 1) res += high * digit + low + 1;
            else if(cur > 1) res += high * digit + digit;
            low += cur * digit;
            cur = high % 10;
            high /= 10;
            digit = digit * 10;
        }
        return res;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
