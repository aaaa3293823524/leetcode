# 剑指 Offer 53 - I. zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof | 在排序数组中查找数字 I

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>统计一个数字在排序数组中出现的次数。</p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> nums = [<code>5,7,7,8,8,10]</code>, target = 8
<strong>输出:</strong> 2</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> nums = [<code>5,7,7,8,8,10]</code>, target = 6
<strong>输出:</strong> 0</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= nums.length <= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup></code></li>
	<li><code>nums</code> 是一个非递减数组</li>
	<li><code>-10<sup>9</sup> <= target <= 10<sup>9</sup></code></li>
</ul>

<p> </p>

<p><strong>注意：</strong>本题与主站 34 题相同（仅返回值不同）：<a href="https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/">https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/</a></p>


## Note

哈希表



二分法


## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int search(int[] nums, int target) {
        // 搜索右边界 right
        int i = 0, j = nums.length - 1;
        while(i <= j) {
            int m = (i + j) / 2;
            if(nums[m] <= target) i = m + 1;
            else j = m - 1;
        }
        int right = i;
        // 若数组中无 target ，则提前返回
        if(j >= 0 && nums[j] != target) return 0;
        // 搜索左边界 right
        i = 0; j = nums.length - 1;
        while(i <= j) {
            int m = (i + j) / 2;
            if(nums[m] < target) i = m + 1;
            else j = m - 1;
        }
        int left = j;
        return right - left - 1;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

[回到目录](../README.md)