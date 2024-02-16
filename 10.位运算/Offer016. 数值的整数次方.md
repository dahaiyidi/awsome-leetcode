## Problem

#### [剑指 Offer 16. 数值的整数次方](https://leetcode.cn/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

实现 [pow(*x*, *n*)](https://www.cplusplus.com/reference/valarray/pow/) ，即计算 x 的 n 次幂函数（即，xn）。不得使用库函数，同时不需要考虑大数问题。

 同[50. Pow(x, n)](https://leetcode.cn/problems/powx-n/)

------

### Note

- 从位的角度理解快速幂
- 如果求x^77 幂表示成为二进制 x^(1001101)=  x^(1000000) *  x^(0001000) *  x^(0000100) *  x^(0000001), 因此可以在位为1的地方乘以相应的元素即可。
- a = x^(0000001) =》 b = x^(0000100) ， 幂的1向左移动了2位，也就是说b项的幂是a项的幂4倍， 也对应了2次x*=x，也就是`x*=x`的次数等于幂的位移
- 也就不难写出程序
- https://leetcode.cn/problems/powx-n/solution/powx-n-by-leetcode-solution/

------

### Complexity

- 时间O：log(n)
- 空间O：1

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    double myPow(double x, int n) {
        // 当n为奇数，x^n = ( x^(n/2) )^2 *x
        // 当n为偶数，x^n = ( x^(n/2) )^2
        // 直到n = 0
        double res = 1;
        long N = n; // 如果最小的负数变成正数时会溢出
        if(N < 0)
        {
            x = 1.0 / x;
            N = -N;
        }

        while(N)
        {
            if(N & 1 == 1)
            {
                res *= x;
            }
             x *= x;
             N >>= 1;
        }
        return res;


    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
