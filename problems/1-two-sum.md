# 1. two-sum | 两数之和

## Question description

<!--If you want to use the English description, use <p>Given an array of integers <code>nums</code>&nbsp;and an integer <code>target</code>, return <em>indices of the two numbers such that they add up to <code>target</code></em>.</p>

<p>You may assume that each input would have <strong><em>exactly</em> one solution</strong>, and you may not use the <em>same</em> element twice.</p>

<p>You can return the answer in any order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,7,11,15], target = 9
<strong>Output:</strong> [0,1]
<strong>Output:</strong> Because nums[0] + nums[1] == 9, we return [0, 1].
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,2,4], target = 6
<strong>Output:</strong> [1,2]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,3], target = 6
<strong>Output:</strong> [0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>3</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= target &lt;= 10<sup>9</sup></code></li>
	<li><strong>Only one valid answer exists.</strong></li>
</ul>
 instead-->
<p>给定一个整数数组 <code>nums</code>&nbsp;和一个目标值 <code>target</code>，请你在该数组中找出和为目标值的那&nbsp;<strong>两个</strong>&nbsp;整数，并返回他们的数组下标。</p>

<p>你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre>给定 nums = [2, 7, 11, 15], target = 9

因为 nums[<strong>0</strong>] + nums[<strong>1</strong>] = 2 + 7 = 9
所以返回 [<strong>0, 1</strong>]
</pre>




## Solution

Language: **python3**  /  Runtime: 40 ms

```python3
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashtable = dict()
        for i, num in enumerate(nums):
            if target - num in hashtable:
                return [hashtable[target - num], i]
            hashtable[nums[i]] = i
        return []


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/two-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/two-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/two-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/two-sum/)

[回到目录](../README.md)