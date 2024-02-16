## Problem

#### [剑指 Offer 59 - II. 队列的最大值](https://leetcode.cn/problems/dui-lie-de-zui-da-zhi-lcof/)

请定义一个队列并实现函数 `max_value` 得到队列里的最大值，要求函数`max_value`、`push_back` 和 `pop_front` 的**均摊**时间复杂度都是O(1)。

若队列为空，`pop_front` 和 `max_value` 需要返回 -1

**示例 1：**

```
输入: 
["MaxQueue","push_back","push_back","max_value","pop_front","max_value"]
[[],[1],[2],[],[],[]]
输出: [null,null,null,2,1,2]
```

**示例 2：**

```
输入: 
["MaxQueue","pop_front","max_value"]
[[],[],[]]
输出: [null,-1,-1]
```

 

------

### Note

- 一开始被题目复杂的要求吓到了，其实逻辑非常简单。
- 只是需要寻求一个合适的数据结构存储当前队列的最大值即可： 
  - 使用一个双向链表ls记录当前的max value， ls是一个递减的链表
  - 当来一个新的value， 在ls中 < cur value的元素均不会作为max value，需要将< cur value的元素 pop
  - （当value < ls的最后一个元素，则直接将value加入即可）
  - ls.front()是max value


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
class MaxQueue {
public:
    queue<int> q;
    list<int> ls;
    MaxQueue() {

    }
    
    int max_value() {
        if(ls.empty())
        {
            return -1;
        }
        return ls.front();
    }
    
    void push_back(int value) {
        q.push(value);
        while(!ls.empty() && ls.back() < value)
        {
            ls.pop_back();
        }
        ls.push_back(value);
    }
    
    int pop_front() {
        if(q.empty())
        {
            return -1;
        }
        int res = q.front();
        q.pop();

        if(res == ls.front())
        {
            ls.pop_front();
        }
        
        return res;
    }
};

/**
 * Your MaxQueue object will be instantiated and called as such:
 * MaxQueue* obj = new MaxQueue();
 * int param_1 = obj->max_value();
 * obj->push_back(value);
 * int param_3 = obj->pop_front();
 */
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
