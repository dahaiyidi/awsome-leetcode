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
    int res;
    int k;
    void dfs(TreeNode* root)
    {
        if(!root)
        {
            return;
        }

        dfs(root->right);
        
        // 这是核心处理程序
        --k;
        if(k == 0)
        {
            res = root->val;
            cout << res << endl;
            return;
        }

        dfs(root->left);
    }
    int kthLargest(TreeNode* root, int k) {
        // 右中左遍历
        this->k = k;
        dfs(root);
        return res;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
