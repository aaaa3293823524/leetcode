# 4. median-of-two-sorted-arrays | 寻找两个正序数组的中位数

## Question description

<!--If you want to use the English description, use <p>Given two sorted arrays <code>nums1</code> and <code>nums2</code> of size <code>m</code> and <code>n</code> respectively, return <strong>the median</strong> of the two sorted arrays.</p>

<p>The overall run time complexity should be <code>O(log (m+n))</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,3], nums2 = [2]
<strong>Output:</strong> 2.00000
<strong>Explanation:</strong> merged array = [1,2,3] and median is 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,2], nums2 = [3,4]
<strong>Output:</strong> 2.50000
<strong>Explanation:</strong> merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>nums1.length == m</code></li>
	<li><code>nums2.length == n</code></li>
	<li><code>0 &lt;= m &lt;= 1000</code></li>
	<li><code>0 &lt;= n &lt;= 1000</code></li>
	<li><code>1 &lt;= m + n &lt;= 2000</code></li>
	<li><code>-10<sup>6</sup> &lt;= nums1[i], nums2[i] &lt;= 10<sup>6</sup></code></li>
</ul>
 instead-->
<p>给定两个大小分别为 <code>m</code> 和 <code>n</code> 的正序（从小到大）数组&nbsp;<code>nums1</code> 和&nbsp;<code>nums2</code>。请你找出并返回这两个正序数组的 <strong>中位数</strong> 。</p>

<p>算法的时间复杂度应该为 <code>O(log (m+n))</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums1 = [1,3], nums2 = [2]
<strong>输出：</strong>2.00000
<strong>解释：</strong>合并数组 = [1,2,3] ，中位数 2
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums1 = [1,2], nums2 = [3,4]
<strong>输出：</strong>2.50000
<strong>解释：</strong>合并数组 = [1,2,3,4] ，中位数 (2 + 3) / 2 = 2.5
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums1 = [0,0], nums2 = [0,0]
<strong>输出：</strong>0.00000
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>nums1 = [], nums2 = [1]
<strong>输出：</strong>1.00000
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>nums1 = [2], nums2 = []
<strong>输出：</strong>2.00000
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>nums1.length == m</code></li>
	<li><code>nums2.length == n</code></li>
	<li><code>0 &lt;= m &lt;= 1000</code></li>
	<li><code>0 &lt;= n &lt;= 1000</code></li>
	<li><code>1 &lt;= m + n &lt;= 2000</code></li>
	<li><code>-10<sup>6</sup> &lt;= nums1[i], nums2[i] &lt;= 10<sup>6</sup></code></li>
</ul>




## Solution

Language: **python3**  /  Runtime: 132 ms

```python3
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        if nums1 == None and nums2 == None:
            return False
        for i in nums2:
            nums1.append(i)
        nums1.sort()
        return self.median(nums1)
        
    def median(self, nums):
        if not nums or len(nums) <= 0:
            return 0
        length = len(nums)
        if length % 2 == 1:
            return nums[length//2]
        else:
            return (nums[length//2-1] + nums[length//2]) / 2.0
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/description/)

Solution: [LeetCode](https://leetcode.com/articles/median-of-two-sorted-arrays/)  /  [LeetCode中国](https://leetcode-cn.com/articles/median-of-two-sorted-arrays/)

[回到目录](../README.md)