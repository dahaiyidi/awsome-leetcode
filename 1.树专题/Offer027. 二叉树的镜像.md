## Problem

#### [剑指 Offer 27. 二叉树的镜像](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/)

简单

请完成一个函数，输入一个二叉树，该函数输出它的镜像。



------

### Note

- 两大题型，不会用到遍历，那就用到递归。

------

### Complexity

- 时间O：n
- 空间O：最坏情况下为链表，n；平均情况下为logn

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    TreeNode* mirrorTree(TreeNode* root) {
        if(root == NULL)
        {
            return root;
        }
        TreeNode* tmp = root->left;
        root->left = root->right;
        root->right = tmp;
        // 递归处理子树
        mirrorTree(root->left);
        mirrorTree(root->right);
        return root;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
