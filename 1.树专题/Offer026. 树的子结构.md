## Problem

#### [剑指 Offer 26. 树的子结构](https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof/)

中等

输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)

B是A的子结构， 即 A中有出现和B相同的结构和节点值。

例如:
 给定的树 A:

`   3   / \   4  5  / \ 1  2`
 给定的树 B：

`  4  / 1`
 返回 true，因为 B 与 A 的一个子树拥有相同的结构和节点值。

------

### Note

- 递归
- 将判断逻辑处理好即可
- 两种情况：
  - 如果是A当前节点与B 匹配上
  - 若A当前节点与B不能匹配上：
    - A->left 中是否包含B
    - A->right 中是否包含B


------

### Complexity

- 时间O：MN， M，N分别为AB树节点数目
- 空间O：M

------

### Python

```python

```

### C++

```C++

class Solution {
public:
    bool fun(TreeNode* r1, TreeNode* r2)
    {
        // 函数定义是：判断如果将r2根节点和r1根节点放在一起，全部r2节点 与r1对应部位的节点值一致
        if(!r2)  
        {
            return true;
        }

        if(!r1)
        {
            return false;
        }

        if(r1->val != r2->val)
        {
            return false;
        }

        return fun(r1->left, r2->left) && fun(r1->right, r2->right);

    }
    bool isSubStructure(TreeNode* A, TreeNode* B) {
        if(!A || !B)
            return false;
        
        return fun(A, B) || isSubStructure(A->left, B) || isSubStructure(A->right, B);       

    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
