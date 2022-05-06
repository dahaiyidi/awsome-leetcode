## Problem

#### [剑指 Offer II 029. 排序的循环链表](https://leetcode-cn.com/problems/4ueAj6/)

++

难度中等16

给定**循环单调非递减列表**中的一个点，写一个函数向这个列表中插入一个新元素 `insertVal` ，使这个列表仍然是循环升序的。

给定的可以是这个列表中任意一个顶点的指针，并不一定是这个列表中最小元素的指针。

如果有多个满足条件的插入位置，可以选择任意一个位置插入新的值，插入后整个列表仍然保持有序。

如果列表为空（给定的节点是 `null`），需要创建一个循环有序列表并返回这个节点。否则。请返回原先给定的节点。



------

### Note

- 插入的点有两种：1）在链表内部找到合适的位置插入；2）在边界点插入：大于最大值 or 小于最大值
- while的条件为：p.next != head

------

### Complexity

- 时间O：n
- 空间O：1

------

### Python

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, next=None):
        self.val = val
        self.next = next
"""

class Solution:
    def insert(self, head: 'Node', insertVal: int) -> 'Node':
        if not head:
            tmp = Node(insertVal)
            tmp.next = tmp
            return tmp

        p = head
        while p.next != head:
            if p.val > p.next.val: # 到达边界点
                if p.val < insertVal or insertVal < p.next.val: # 大于最大值 or 小于最小值
                    break
            
            if p.val <= insertVal and insertVal <= p.next.val: # 在内部找到可以满足的插入点
                break

            p = p.next 
        
        p.next = Node(insertVal, p.next)
        return head
        
```

### C++

```C++

class Solution {
public:
    Node* insert(Node* head, int insertVal) {
        if(!head){
            Node* tmp = new Node(insertVal);
            tmp->next = tmp;
            return tmp;
        }
        Node* p = head;
        while(p->next != head){ // 避免陷入死循环
            if(p->val > p->next->val){
                // 进入分界点
                if(p->val < insertVal || insertVal < p->next->val){
                    break;
                }
            }
            if(p->val <= insertVal && insertVal <= p->next->val){
                // 在内部找到适合插入的点
                break;
            }
            p = p->next;
        }
        p->next = new Node(insertVal, p->next);
        return head;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode

