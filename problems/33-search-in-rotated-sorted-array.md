# 33. search-in-rotated-sorted-array | 搜索旋转排序数组

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>nums</code> sorted in ascending order, and an integer <code>target</code>.</p>

<p>Suppose that <code>nums</code> is rotated at some pivot unknown to you beforehand (i.e., <code>[0,1,2,4,5,6,7]</code> might become <code>[4,5,6,7,0,1,2]</code>).</p>

<p><em>If <code>target</code> is found in the array return its index, otherwise, return <code>-1</code>.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [4,5,6,7,0,1,2], target = 0
<strong>Output:</strong> 4
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [4,5,6,7,0,1,2], target = 3
<strong>Output:</strong> -1
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [1], target = 0
<strong>Output:</strong> -1
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5000</code></li>
	<li><code>-10^4 &lt;= nums[i] &lt;= 10^4</code></li>
	<li>All values of <code>nums</code> are <strong>unique</strong>.</li>
	<li><code>nums</code> is guranteed to be rotated at some pivot.</li>
	<li><code>-10^4 &lt;= target &lt;= 10^4</code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>nums</code> ，和一个整数 <code>target</code> 。</p>

<p>该整数数组原本是按升序排列，但输入时在预先未知的某个点上进行了旋转。（例如，数组 <code>[0,1,2,4,5,6,7]</code> 可能变为 <code>[4,5,6,7,0,1,2]</code> ）。</p>

<p>请你在数组中搜索 <code>target</code> ，如果数组中存在这个目标值，则返回它的索引，否则返回 <code>-1</code> 。</p>
 

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [<code>4,5,6,7,0,1,2]</code>, target = 0
<strong>输出：</strong>4
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [<code>4,5,6,7,0,1,2]</code>, target = 3
<strong>输出：</strong>-1</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [1], target = 0
<strong>输出：</strong>-1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 5000</code></li>
	<li><code>-10^4 <= nums[i] <= 10^4</code></li>
	<li><code>nums</code> 中的每个值都 <strong>独一无二</strong></li>
	<li><code>nums</code> 肯定会在某个点上旋转</li>
	<li><code>-10^4 <= target <= 10^4</code></li>
</ul>


## Note

二分查找


## Solution

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if not nums:
            return -1
        l, r = 0, len(nums) - 1
        while l <= r:
            mid = (l + r) // 2
            if nums[mid] == target:
                return mid
            if nums[0] <= nums[mid]:
                if nums[0] <= target < nums[mid]:
                    r = mid - 1
                else:
                    l = mid + 1
            else:
                if nums[mid] < target <= nums[len(nums) - 1]:
                    l = mid + 1
                else:
                    r = mid - 1
        return -1


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/search-in-rotated-sorted-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/search-in-rotated-sorted-array/)

[回到目录](../README.md)