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
    int target = 0;
public:

    int partition(vector<int>& nums, int left, int right)
    {
        int k = left + (rand() % (right - left + 1));
        int val = nums[k];
        swap(nums[k], nums[right]);
        int i = left;
        int j = left;
        for(j = left; j < right; ++j)
        {
            if(nums[j] < val)
            {
                swap(nums[i++], nums[j]);
            }
        }
        swap(nums[i], nums[right]);
        return i; // i是分界点
    }
    
    void quickSort(vector<int>& nums, int left, int right)
    {
        if(left >= right)
        {
            return;
        }
        int i = partition(nums, left, right);
        if(i == target)
        {
            return;
        }
        else if(target < i)
        {
            right = i - 1;
        }
        else if(target > i)
        {
            left = i + 1;
        }

        quickSort(nums, left, right);

        // quickSort(nums, left, i - 1);
        // quickSort(nums, i + 1, right);
    }

    vector<int> getLeastNumbers(vector<int>& arr, int k) {
        target = k - 1;
        quickSort(arr, 0, arr.size() - 1);
        return vector<int>(arr.begin(), arr.begin() + k);
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
