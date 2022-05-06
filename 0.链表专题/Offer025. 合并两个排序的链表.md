## Problem

#### [剑指 Offer 25. 合并两个排序的链表](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

简单

输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。

**示例1：**

```
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```

**限制：**

```
0 <= 链表长度 <= 1000
```

------

### Note

- 思路不难

------

### Complexity

- 时间O：n + m
- 空间O：1

------

### Python

```python

```

### C++

```C++

class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* dummy = new ListNode(-1);
        ListNode* pre = dummy;
        while(l1 && l2)
        {
            if(l1->val < l2->val)
            {
                pre->next = l1;
                l1 = l1->next;
                pre = pre->next;
            }
            else
            {
                pre->next = l2;
                l2 = l2->next;
                pre = pre->next;
            }
        }
        if(l1)
        {
            pre->next = l1;
        }
        if(l2)
        {
            pre->next = l2;
        }
        return dummy->next;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
