## Problem

#### [剑指 Offer 18. 删除链表的节点](https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/)

简单

给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。

返回删除后的链表的头节点。

**注意：**此题对比原题有改动

- 题目保证链表中节点的值互不相同
- 若使用 C 或 C++ 语言，你不需要 `free` 或 `delete` 被删除的节点

------

### Note

- 思路不难

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
    ListNode* deleteNode(ListNode* head, int val) {
        ListNode* dummy = new ListNode(-1);
        dummy->next = head;
        ListNode* p = dummy;
        
        while(p && p->next && p->next->val != val)
        {
            p = p->next;
        }

        if(p->next)
        {
            p->next = p->next->next;
        }
        // if p 已经到达了最后一个节点，说明不存在要删除的值
        // return dummy->next;  
        ListNode* h = dummy->next;
        delete dummy;
        return h;

    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
