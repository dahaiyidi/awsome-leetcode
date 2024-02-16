## Problem

#### [剑指 Offer 30. 包含min函数的栈](https://leetcode.cn/problems/bao-han-minhan-shu-de-zhan-lcof/)

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

 同：[155. 最小栈](https://leetcode.cn/problems/min-stack/)

------

### Note

- 问题不难，但是需要注意的是：
   - 不用记录截止到当前的最小值，因为st.top()就是最小值
   - 当x<= st2.top()就可以加入到st2中
   - 在pop时，若st1.top() == st2.top()时，就可以直接pop st2了。


------

### Complexity

- 时间O：1
- 空间O：n

------

### Python

```python

```

### C++

```C++
class MinStack {
public:
    stack<int> A, B; // B用来存储 当前的min
    MinStack() {}
    void push(int x) {
        A.push(x);
        if(B.empty() || B.top() >= x)  ////////////////// top ,pop 记得empty检验
            B.push(x);
    }
    void pop() {
        if(A.top() == B.top())
            B.pop();
        A.pop();
    }
    int top() {
        return A.top();
    }
    int getMin() {
        return B.top();
    }
};

作者：Krahets
链接：https://leetcode.cn/problems/bao-han-minhan-shu-de-zhan-lcof/solutions/133760/mian-shi-ti-30-bao-han-minhan-shu-de-zhan-fu-zhu-z/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
