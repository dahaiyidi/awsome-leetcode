## Problem

#### [剑指 Offer 24. 反转链表](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)

简单

定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

 

**示例:**

```c++
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
```

 

------

### Note

- 反转链表是相当经典的题目，其中的翻转思路在很多题目中都有用到。
- 但是翻转链表一点也不难，只要将下图画出来，一切都跃然纸上。
- 关键点：
  - 使用dummy简化问题
  - 找到pre，p, cur的节点，根据更新方式更新即可。3个节点的图如下，非常简单。
  - ![image-20220506103758946](imgs/image-20220506103758946.png)


------

### Complexity

- 时间O：N
- 空间O：1

------

### Python

```python

```

### C++

```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(!head || !head->next)
        {
            return head;
        }

        ListNode* dummy = new ListNode(-1);
        dummy->next = head;

        ListNode* pre = dummy;
        ListNode* p = head;
        ListNode* cur = head->next;
        while(cur)
        {
            p->next = cur->next;
            cur->next = pre->next;
            pre->next = cur;
            cur = p->next;
        } 
        head = dummy->next;
        delete dummy;
        return head;
    }
};
```



点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
