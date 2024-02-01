## Problem

#### [剑指 Offer 11. 旋转数组的最小数字](https://leetcode.cn/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)

简单++

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。

给你一个可能存在 **重复** 元素值的数组 `numbers` ，它原来是一个升序排列的数组，并按上述情形进行了一次旋转。请返回旋转数组的**最小元素**。例如，数组 `[3,4,5,1,2]` 为 `[1,2,3,4,5]` 的一次旋转，该数组的最小值为 1。 

注意，数组 `[a[0], a[1], a[2], ..., a[n-1]]` 旋转一次 的结果为数组 `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]` 。

示例 1：

输入：numbers = [3,4,5,1,2]
输出：1

示例 2：

输入：numbers = [2,2,2,0,1]
输出：0

同[154. 寻找旋转排序数组中的最小值 II](https://leetcode.cn/problems/find-minimum-in-rotated-sorted-array-ii/)

------

### Note

- 部分有序，显然要使用二分法，但是问题是题目中也没有target, nums[mid]应该与谁比较值呢？
- 可以选择num[right]
- 比较难处理的是num[mid] = num[right]的情况，我们还要缩小范围，虽然缩小一半的目的是达不到了，但是我们right--后，目标值肯定还是在[left, right]范围中。因此，可以选择right--

------

### Complexity

- 时间O：n
- 空间O：logn，最坏为n

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    int minArray(vector<int>& numbers) {
        int i = 0;
        int j = numbers.size() - 1;
        if(numbers[i] < numbers[j])
        {
            return numbers[i];
        }

        while(i <= j)
        {
            int mid = i + ((j - i) >> 1);
            if(numbers[mid] > numbers[j])
            {
                i = mid + 1;
            }
            else if(numbers[mid] < numbers[j])
            {
                j = mid; // mid 处可能是所要求的最小值, 若直接-1， 则有可能直接跳过了最小值，导致永远无法找到该值。 而numbers[mid] > numbers[j]情况下则没有这种问题。
            }
            else 
            {
                --j; //相等的时候则难以判断，但是可以肯定地是j--后， 最小值还在[i, j]范围内，那就j--缩小范围。
            }
        }
        return numbers[i];
    }
};
```



From : https://github.com/dahaiyidi/awsome-leetcode
