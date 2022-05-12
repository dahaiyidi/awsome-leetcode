## Problem

#### [剑指 Offer 51. 数组中的逆序对](https://leetcode.cn/problems/shu-zu-zhong-de-ni-xu-dui-lcof/)

困难++

在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。

------

### Note

- 思路不难，只要稳定的排序算法即可——插入排序，归并排序
- 插入排序时间复杂度为n^2
- 归并排序时间复杂度为nlogn, 在归并排序的一个地方添加一句即可。
- 建议与[912. 排序数组](https://leetcode-cn.com/problems/sort-an-array/)一起食用。

------

### Complexity

- 时间O：nlogn
- 空间O：n

------

### Python

```python

```

### C++

```C++
class Solution {
private:
    int count = 0;
public:
    void mergeTwo(vector<int>& nums, int left, int mid, int right, vector<int>& tmp)
    {
        int i = left;
        int j = mid + 1;
        int k = left;
        while(i <= mid && j <= right)
        {
            if(nums[i] <= nums[j])
            {
                tmp[k++] = nums[i++];
            }
            else if(nums[i] > nums[j])
            {
                tmp[k++] = nums[j++];
                count += (mid - i + 1); // 此处发现逆序对,有序左半边的子数组还剩下mid-i+1个数字，而处于后面的nums[j]则跨越了它们跑到了它们前面。对应了逆序对的个数
            }
        }
        while(i <= mid)
        {
            tmp[k++] = nums[i++];
        }

        while(j <= right)
        {
            tmp[k++] = nums[j++];
        }

        for(i = left; i <= right; ++i)
        {
            nums[i] = tmp[i];
        }
    }
    void mergeSort(vector<int>& nums, int left, int right, vector<int>& tmp)
    {
        if(left >= right)
        {
            return;
        }
        int mid = left + ((right - left) >> 1);
        mergeSort(nums, left, mid, tmp);
        mergeSort(nums, mid + 1, right, tmp);
        mergeTwo(nums, left, mid, right, tmp);
    }
    int reversePairs(vector<int>& nums) {
        // 插入排序会超时，因为是平方时间复杂度
        // 使用归并排序，时间复杂度为nlogn,也是稳定的排序算法。
        vector<int> tmp(nums.size(), 0);
        mergeSort(nums, 0, nums.size() - 1, tmp);
        return count;

    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
