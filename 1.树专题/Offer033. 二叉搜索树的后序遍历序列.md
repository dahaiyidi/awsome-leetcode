## Problem

#### [剑指 Offer 33. 二叉搜索树的后序遍历序列](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)

中等++

输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 `true`，否则返回 `false`。假设输入的数组的任意两个数字都互不相同。

 

------

### Note

- 思路挺绕
- 思路：https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/solution/mian-shi-ti-33-er-cha-sou-suo-shu-de-hou-xu-bian-6/

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
// 迭代法：
//时间：N2
// 空间： n
class Solution {
public:
    bool verifyTreeOrder(vector<int>& postorder) {
        return func(postorder, 0, postorder.size() -1);

    }
    bool func(vector<int>& postorder, int i, int j)
    {
        if(i >= j) return true;
        int p = i;
        while(postorder[p] < postorder[j]) p++;
        int m = p;
        while(postorder[p] > postorder[j]) p++;
        return p == j && func(postorder, i, m - 1) && func(postorder, m, j -1);
    }

};

// 栈
class Solution {
public:
    bool verifyPostorder(vector<int>& postorder) {
        // 后序遍历：左右根
        // 一个关键点：对于所有节点，左子树所有点都小于根节点。 从后往前，第一个下降的就是左开始的地方，那么就回退找到该左的父，判断左里面的值是否都小于父。父是刚大于左的根的值。

        // 从右到左遍历，不停地将值加入stack，找到第一个下降的点postorder[i] < postorder[i + 1]， 那么postorder[i]应该是左子树的根节点
        // 找到父节点：从stack中弹出节点， 刚好大于postorder[i]（最后一个被pop出来的点）的为父节点。
        // 继续i深入左子树，左子树中所有的点均不能大于该父节点  （刚开始时，可以设置root的值为正无穷，也就是把当前树当作正无穷的左子树）
        // 如果发现有值大于父节点，则返回false；如果可以完成遍历，则返回true
        stack<int> st;
        int root = INT_MAX;
        for(int i = postorder.size() - 1; i >= 0; --i)
        {
            if(postorder[i] > root)
            {
                return false;
            }
            while(!st.empty() && postorder[i] < st.top())  // 注意此处的条件
            {
                root = st.top();
                st.pop();
            }
            st.push(postorder[i]);
        }
        return true;
    }
};



// 构建bst的思想。判断值是否在某个范围内。
// 时间：n， 空间n
class Solution {
public:
    void build(vector<int>& postorder, int low, int high)
    {
        if(postorder.empty()) return;
        int val = postorder[postorder.size() - 1];
        if(val <= low || val >= high) return;
        postorder.pop_back();
        build(postorder, val, high);
        build(postorder, low, val);
    }
    bool verifyTreeOrder(vector<int>& postorder) {
        build(postorder, INT_MIN, INT_MAX);
        return postorder.empty();
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
