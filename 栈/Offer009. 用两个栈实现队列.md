## Problem

#### [剑指 Offer 09. 用两个栈实现队列](https://leetcode.cn/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 `appendTail` 和 `deleteHead` ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，`deleteHead` 操作返回 -1 )

------

### Note

- 问题不难，但是需要注意的是：

- ```c++
   // 注意在appendTail时，不需要将st2的全部元素倒腾到st1
  // 注意在deleteHead时，不需要将st1的全部元素倒腾到st2
  ```

  

------

### Complexity

- 时间O：append为1， delete最差为n
- 空间O：n

------

### Python

```python

```

### C++

```C++
class CQueue {
public:
    stack<int> st1;
    stack<int> st2;

    CQueue() {

    }
    
    void appendTail(int value) {
        // 注意在appendTail时，不需要将st2的全部元素倒腾到st1
        st1.push(value);
    }
    
    int deleteHead() {
        // 注意在deleteHead时，不需要将st1的全部元素倒腾到st2
        if(st2.empty())
        {
            // st2为空，不停地从st1转移到st2
            while(!st1.empty())
            {
                st2.push(st1.top());
                st1.pop();
            }
        }

        if(st2.empty())
        {
            // st1和st2均为空
            return -1;
        }
        int val = st2.top();
        st2.pop();
        return val;
    }
};

/**
 * Your CQueue object will be instantiated and called as such:
 * CQueue* obj = new CQueue();
 * obj->appendTail(value);
 * int param_2 = obj->deleteHead();
 */
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
