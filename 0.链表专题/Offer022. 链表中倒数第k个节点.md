## Problem

#### [剑指 Offer 22. 链表中倒数第k个节点](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

简单

输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。

例如，一个链表有 `6` 个节点，从头节点开始，它们的值依次是 `1、2、3、4、5、6`。这个链表的倒数第 `3` 个节点是值为 `4` 的节点。

 

------

### Note

- 思路不难
- 

------

### Complexity

- 时间O：n
- 空间O：1

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    ListNode* getKthFromEnd(ListNode* head, int k) {
        ListNode* p1 = head;
        ListNode* p2 = head;
        // 移动k-1次，到达第k个节点
        for(int i = 0; i < k - 1 && p2; ++i)
        {
            p2 = p2->next;
        }
        // 此时节点数<k,直接返回
        if(p2 == NULL)
        {
            return head;
        }

        while(p2 && p2->next)
        {
            p1 = p1->next;
            p2 = p2->next;
        }
        return p1;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
