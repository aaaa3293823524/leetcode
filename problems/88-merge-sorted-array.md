# 88. merge-sorted-array | 合并两个有序数组

## Question description

<!--If you want to use the English description, use <p>Given two sorted integer arrays <em>nums1</em> and <em>nums2</em>, merge <em>nums2</em> into <em>nums1</em> as one sorted array.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>The number of elements initialized in <em>nums1</em> and <em>nums2</em> are <em>m</em> and <em>n</em> respectively.</li>
	<li>You may assume that <em>nums1</em> has enough space (size that is&nbsp;<strong>equal</strong> to <em>m</em> + <em>n</em>) to hold additional elements from <em>nums2</em>.</li>
</ul>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

<strong>Output:</strong>&nbsp;[1,2,2,3,5,6]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-10^9 &lt;= nums1[i], nums2[i] &lt;= 10^9</code></li>
	<li><code>nums1.length == m + n</code></li>
	<li><code>nums2.length == n</code></li>
</ul>
 instead-->
<p>给你两个有序整数数组 <em>nums1 </em>和 <em>nums2</em>，请你将 <em>nums2 </em>合并到 <em>nums1 </em>中<em>，</em>使 <em>nums1 </em>成为一个有序数组。</p>

<p> </p>

<p><strong>说明：</strong></p>

<ul>
	<li>初始化 <em>nums1</em> 和 <em>nums2</em> 的元素数量分别为 <em>m</em> 和 <em>n </em>。</li>
	<li>你可以假设 <em>nums1 </em>有足够的空间（空间大小大于或等于 <em>m + n</em>）来保存 <em>nums2</em> 中的元素。</li>
</ul>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

<strong>输出：</strong>[1,2,2,3,5,6]</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>-10^9 <= nums1[i], nums2[i] <= 10^9</code></li>
	<li><code>nums1.length == m + n</code></li>
	<li><code>nums2.length == n</code></li>
</ul>




## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: void Do not return anything, modify nums1 in-place instead.
        """
        # Make a copy of nums1.
        nums1_copy = nums1[:m] 
        nums1[:] = []

        # Two get pointers for nums1_copy and nums2.
        p1 = 0 
        p2 = 0
        
        # Compare elements from nums1_copy and nums2
        # and add the smallest one into nums1.
        while p1 < m and p2 < n: 
            if nums1_copy[p1] < nums2[p2]: 
                nums1.append(nums1_copy[p1])
                p1 += 1
            else:
                nums1.append(nums2[p2])
                p2 += 1

        # if there are still elements to add
        if p1 < m: 
            nums1[p1 + p2:] = nums1_copy[p1:]
        if p2 < n:
            nums1[p1 + p2:] = nums2[p2:]


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/merge-sorted-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/merge-sorted-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/merge-sorted-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/merge-sorted-array/)

[回到目录](../README.md)