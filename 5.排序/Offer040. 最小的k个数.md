## Problem

#### [剑指 Offer 40. 最小的k个数](https://leetcode.cn/problems/zui-xiao-de-kge-shu-lcof/)

简单++

输入整数数组 `arr` ，找出其中最小的 `k` 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

 

**示例 1：**

```
输入：arr = [3,2,1], k = 2
输出：[1,2] 或者 [2,1]
```

**示例 2：**

```
输入：arr = [0,1,2,1], k = 1
输出：[0]
```

 

------

### Note

- 不难，对快排稍微变形即可。

------

### Complexity

- 时间O：**平均为n**，最坏为n^2
- 空间O：平均为logn, 最坏为n

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    int partition(vector<int>& nums, const int left, const int right)
    {
        int pivot = (rand() % (right - left + 1)) + left;
        swap(nums[pivot], nums[right]);
        int pivot_val = nums[right];
        int i = left;
        int j = right -1;
        while(true)
        {
            while(i <= right -1 && nums[i] < pivot_val) i++;
            while(j >= left && nums[j] > pivot_val) j--;
            if(i >= j) break;
            swap(nums[i], nums[j]);
            i++;
            j--;
        }
        swap(nums[i], nums[right]);
        return i;
    }
    void quickSort(vector<int>& nums, const int left, const int right, const int target_ind)
    {
        if(left >= right) return;
        int i = partition(nums, left, right);
        if (i == target_ind) return;
        else if(i < target_ind) quickSort(nums, i + 1, right, target_ind);
        else if(i > target_ind) quickSort(nums, left, i - 1, target_ind);
    }
    vector<int> inventoryManagement(vector<int>& nums, int cnt) {
        if(nums.empty() || cnt == nums.size()) return nums;
        quickSort(nums, 0, nums.size() -1, cnt - 1);
        return vector<int>(nums.begin(), nums.begin() + cnt);
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
