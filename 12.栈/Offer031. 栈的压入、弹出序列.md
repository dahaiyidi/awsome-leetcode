## Problem

#### [剑指 Offer 31. 栈的压入、弹出序列](https://leetcode.cn/problems/zhan-de-ya-ru-dan-chu-xu-lie-lcof/)

输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如，序列 {1,2,3,4,5} 是某栈的压栈序列，序列 {4,5,3,2,1} 是该压栈序列对应的一个弹出序列，但 {4,3,5,1,2}  就不可能是该压栈序列的弹出序列。https://leetcode.cn/problems/min-stack/)

同：[946. 验证栈序列](https://leetcode.cn/problems/validate-stack-sequences/) 

------

### Note

- 见code


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
    bool validateStackSequences(vector<int>& pushed, vector<int>& popped) {
        stack<int> st;
        int j = 0;
        for(int i = 0; i < pushed.size(); ++i)
        {
            st.push(pushed[i]);
            while(!st.empty() && st.top() == popped[j])
            {
                st.pop();
                ++j;
            }

        }
        return st.empty();
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
