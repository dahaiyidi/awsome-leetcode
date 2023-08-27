## Problem

#### [剑指 Offer 54. 二叉搜索树的第k大节点](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

简单++

给定一棵二叉搜索树，请找出其中第 `k` 大的节点的值。

------

### Note

- 右中左遍历

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
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int kthLargest(TreeNode* root, int k) {

        stack<TreeNode*> s;
        int num = 0;
        while(!s.empty() || root)
        {
            while(root)
            {
                s.push(root);
                root = root->right;
            }

            root = s.top();
            s.pop();
            ++num;
            if(num == k)
            {
                break;
            }
            root = root->left;
        }
        return root->val;

    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
