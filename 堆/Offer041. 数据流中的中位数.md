## Problem

#### [剑指 Offer 41. 数据流中的中位数](https://leetcode.cn/problems/shu-ju-liu-zhong-de-zhong-wei-shu-lcof/)

++

如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。

例如，

[2,3,4] 的中位数是 3

[2,3] 的中位数是 (2 + 3) / 2 = 2.5

设计一个支持以下两种操作的数据结构：

- void addNum(int num) - 从数据流中添加一个整数到数据结构中。
- double findMedian() - 返回目前所有元素的中位数。

------

### Note

- 使用大顶堆记录左半边的数据，使用小顶堆记录右半边的数据。

- 注意：在插入数据的时候，每个数字都需要经过两个堆

- 注意堆的使用方式。

- **进阶**

      如果数据流中所有整数都在 0 到 100 范围内，你将如何优化你的算法？

  可以使用建立长度为 101的桶，每个桶分别统计每个数的出现次数，同时记录数据流中总的元素数量，每次查找中位数时，先计算出中位数是第几位，从前往后扫描所有的桶得到答案。

  这种做法相比于对顶堆做法，计算量上没有优势，**更多的是空间上的优化**。

  对顶堆解法两个操作中耗时操作复杂度为 O(log⁡n)，log 操作常数不会超过 3，在极限数据 10^7 情况下计算量仍然低于耗时操作复杂度为 O(C)（C 固定为 101）桶计数解法。

      如果数据流中 99% 的整数都在 0 到 100 范围内，你将如何优化你的算法？

  和上一问解法类似，对于 111% 采用哨兵机制进行解决即可，**在常规的最小桶和最大桶两侧分别维护一个有序序列**，即建立一个代表负无穷和正无穷的桶。

  上述两个进阶问题的代码如下，但注意由于真实样例的数据分布不是进阶所描述的那样（不是绝大多数都在 `[0,100] `范围内），所以会 TLE。
  链接：https://leetcode.cn/problems/find-median-from-data-stream/solution/gong-shui-san-xie-jing-dian-shu-ju-jie-g-pqy8/

------

### Complexity

- 时间O：插入：logn, 查找1
- 空间O：n

------

### Python

```python

```

### C++

```C++
class MedianFinder {
    priority_queue<int, vector<int>, less<int>> maxHeap;  // 大顶堆， 用于存放左半边的数据
    priority_queue<int, vector<int>, greater<int>> minHeap; // 小顶堆 ，用于存放右半边的数据
public:
    /** initialize your data structure here. */
    MedianFinder() {

    }
    
    void addNum(int num) {
        if(maxHeap.size() == minHeap.size())
        {
            // 偶数个， 最终左半边的存储的多一个元素
            minHeap.push(num);
            maxHeap.push(minHeap.top());
            minHeap.pop();
        }
        else
        {
            // 奇数个， 此时左侧比右侧多一个，先添加到左边，再提取出最大值push到右边
            maxHeap.push(num);
            minHeap.push(maxHeap.top());
            maxHeap.pop();
        }

    }
    
    double findMedian() {
        if(minHeap.size() == maxHeap.size())
        {
            return (minHeap.top() + maxHeap.top()) / 2.0;
        }
        else
        {
            return maxHeap.top();
        }

    }
};

/**
 * Your MedianFinder object will be instantiated and called as such:
 * MedianFinder* obj = new MedianFinder();
 * obj->addNum(num);
 * double param_2 = obj->findMedian();
 */
```



From : https://github.com/dahaiyidi/awsome-leetcode
