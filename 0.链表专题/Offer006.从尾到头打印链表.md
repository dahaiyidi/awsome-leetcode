## Problem

#### [剑指 Offer 06. 从尾到头打印链表](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

简单

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

 

**示例 1：**

```
输入：head = [1,3,2]
输出：[2,3,1]
```

------

### Note

- 思路1：栈
- 思路2：递归
- 当然也可以使用翻转链表的方法。

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
栈版本
class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        vector<int> res;
        stack<int> s;
        while(head)
        {
            s.push(head->val);
            head = head->next;
        }
        while(!s.empty())
        {
            res.push_back(s.top());
            s.pop();
        }
        return res;
    }
};
递归版本：
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
    void func(ListNode* head, vector<int>& res)
    {
        if(head == nullptr) return;
        func(head->next, res);
        res.push_back(head->val);
    }
    vector<int> reverseBookList(ListNode* head) {
        vector<int> res;
        func(head, res);
        return res;
    }
};
```



点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
