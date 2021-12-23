# 334. increasing-triplet-subsequence | 递增的三元子序列

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, return <code>true</code><em> if there exists a triple of indices </em><code>(i, j, k)</code><em> such that </em><code>i &lt; j &lt; k</code><em> and </em><code>nums[i] &lt; nums[j] &lt; nums[k]</code>. If no such indices exists, return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5]
<strong>Output:</strong> true
<strong>Explanation:</strong> Any triplet where i &lt; j &lt; k is valid.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,4,3,2,1]
<strong>Output:</strong> false
<strong>Explanation:</strong> No triplet exists.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1,5,0,4,6]
<strong>Output:</strong> true
<strong>Explanation:</strong> The triplet (3, 4, 5) is valid because nums[3] == 0 &lt; nums[4] == 4 &lt; nums[5] == 6.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>5</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you implement a solution that runs in <code>O(n)</code> time complexity and <code>O(1)</code> space complexity? instead-->
<p>给你一个整数数组 <code>nums</code> ，判断这个数组中是否存在长度为 <code>3</code> 的递增子序列。</p>

<p>如果存在这样的三元组下标 <code>(i, j, k)</code> 且满足 <code>i < j < k</code> ，使得 <code>nums[i] < nums[j] < nums[k]</code> ，返回 <code>true</code> ；否则，返回 <code>false</code> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,3,4,5]
<strong>输出：</strong>true
<strong>解释：</strong>任何 i < j < k 的三元组都满足题意
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [5,4,3,2,1]
<strong>输出：</strong>false
<strong>解释：</strong>不存在满足题意的三元组</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [2,1,5,0,4,6]
<strong>输出：</strong>true
<strong>解释：</strong>三元组 (3, 4, 5) 满足题意，因为 nums[3] == 0 < nums[4] == 4 < nums[5] == 6
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 10<sup>5</sup></code></li>
	<li><code>-2<sup>31</sup> <= nums[i] <= 2<sup>31</sup> - 1</code></li>
</ul>

<p> </p>

<p><strong>进阶：</strong>你能实现时间复杂度为 <code>O(n)</code> ，空间复杂度为 <code>O(1)</code> 的解决方案吗？</p>


## Note

动态规划    每次寻找比当前数小的元素个数   

时间复杂度：O(n^2)

空间复杂度：O(n)



双指针   m1, m2保存两个较小数，找出一个同时大于m1和m2的数即返回。



前后遍历



定义两个数组forward[i]和backward[i]，forward[i]从前向后遍历，保存[0, i]之间最小元素值，backward[i]从后向前遍历，保存[i, size - 1]间最大元素值。然后从前向后遍历，如果找到一个数满足forward[i] < nums[i] < backward[i]，则表示三元子序列存在。

比如：

nums[i]: 8 3 5 1 6

forwa[i]: 8 3 3 1 1

backw[i]:8 6 6 6 6






## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    bool increasingTriplet(vector<int>& nums) {
        int m1 = INT_MAX, m2 = INT_MAX;
        for (auto a : nums) {
            if (m1 >= a) m1 = a;
            else if (m2 >= a) m2 = a;
            else return true;
        }
        return false;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/increasing-triplet-subsequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/increasing-triplet-subsequence/description/)

Solution: [LeetCode](https://leetcode.com/articles/increasing-triplet-subsequence/)  /  [LeetCode中国](https://leetcode-cn.com/articles/increasing-triplet-subsequence/)

[回到目录](../README.md)