## Problem

#### [剑指 Offer 34. 二叉树中和为某一值的路径](https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)

中等++

给你二叉树的根节点 `root` 和一个整数目标和 `targetSum` ，找出所有 **从根节点到叶子节点** 路径总和等于给定目标和的路径。

**叶子节点** 是指没有子节点的节点。

------

### Note

- 递归

------

### Complexity

- 时间O：n， 但是复制vector元素需要耗费n的时间，所以时间复杂度也可以说是n^2
- 空间O：树的高度H

------

### Python

```python

```

### C++

```C++

class Solution {
public:
    void fun(TreeNode* root, int target, vector<vector<int>>& res, vector<int>& path)
    {
        // 节点为null
        if(root == nullptr)
        {
            return;
        }

        int val = root->val;
        path.push_back(val);

        // 到达叶子节点，且符合要求
        if(target == root->val && root->left == nullptr && root->right == nullptr)
        {
            res.push_back(path);
            path.pop_back();  // 注意需要pop， 也可以不写接下来的两行，直接往下走即可。
            return;   
        }

        fun(root->left, target - val, res, path);
        fun(root->right, target - val, res, path);
        path.pop_back();   // 注意需要pop
    }
    vector<vector<int>> pathSum(TreeNode* root, int target) {
        vector<vector<int>> res;
        vector<int> path;
        fun(root, target, res, path);
        return res;
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
