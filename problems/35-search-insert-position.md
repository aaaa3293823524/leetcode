# 35. search-insert-position | 搜索插入位置

## Question description

<!--If you want to use the English description, use <p>Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.</p>

<p>You must&nbsp;write an algorithm with&nbsp;<code>O(log n)</code> runtime complexity.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,5,6], target = 5
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,5,6], target = 2
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,5,6], target = 7
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>nums</code> contains <strong>distinct</strong> values sorted in <strong>ascending</strong> order.</li>
	<li><code>-10<sup>4</sup> &lt;= target &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。</p>

<p>请必须使用时间复杂度为 <code>O(log n)</code> 的算法。</p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> nums = [1,3,5,6], target = 5
<strong>输出:</strong> 2
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> nums = [1,3,5,6], target = 2
<strong>输出:</strong> 1
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> nums = [1,3,5,6], target = 7
<strong>输出:</strong> 4
</pre>

<p><strong>示例 4:</strong></p>

<pre>
<strong>输入:</strong> nums = [1,3,5,6], target = 0
<strong>输出:</strong> 0
</pre>

<p><strong>示例 5:</strong></p>

<pre>
<strong>输入:</strong> nums = [1], target = 0
<strong>输出:</strong> 0
</pre>

<p> </p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 <= nums.length <= 10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> <= nums[i] <= 10<sup>4</sup></code></li>
	<li><code>nums</code> 为<strong>无重复元素</strong>的<strong>升序</strong>排列数组</li>
	<li><code>-10<sup>4</sup> <= target <= 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int l=0,r=nums.length-1;
        while(l<=r){
            int mid=l+(r-l)/2;
            if(nums[mid]==target){
                return mid;
            }
            if(nums[mid]>target)r=mid-1;
            else{
                l=mid+1;
            }
        }
        return l;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/search-insert-position/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/search-insert-position/description/)

Solution: [LeetCode](https://leetcode.com/articles/search-insert-position/)  /  [LeetCode中国](https://leetcode-cn.com/articles/search-insert-position/)

[回到目录](../README.md)