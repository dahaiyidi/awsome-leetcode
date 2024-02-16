## Problem

#### [剑指 Offer 48. 最长不含重复字符的子字符串](https://leetcode.cn/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/)

请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。

同[3. 无重复字符的最长子串](https://leetcode.cn/problems/longest-substring-without-repeating-characters/)

------

### Note

- 双指针+哈希表
- 滑动窗口

------

### Complexity

- 时间O：n
- 空间O：1, 即便使用了unordered_map，但是也仅仅是常数个

------

### Python

```python

```

### C++

```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char, int> mp; // 记录字符对应的索引
        int res = 0;
        int left = 0;
        int right = 0;
        for(int i = 0; i < s.size(); ++i)
        {
            right = i; // 更新当前窗口的right
            if(mp.count(s[i]))
            {
                left = max(left, mp[s[i]] + 1); // 更新窗口的left
            }
            mp[s[i]] = i; // 更新最新的索引
            res = max(res, right - left + 1);
        }
        return res;
    }
};
```

点击链接查看leetcode题目总结。若不总结，则永远陷入刷题的无底洞！**你所畏惧的一切，终将一个个地面对！**

From : :heart: https://github.com/dahaiyidi/awsome-leetcode
