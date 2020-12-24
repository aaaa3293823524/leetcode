# 229. majority-element-ii | 求众数 II

## Question description

<!--If you want to use the English description, use <p>Given an integer array of size <code>n</code>, find all elements that appear more than <code>&lfloor; n/3 &rfloor;</code> times.</p>

<p><strong>Follow-up: </strong>Could you solve the problem&nbsp;in linear time and in O(1) space?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,2,3]
<strong>Output:</strong> [3]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1]
<strong>Output:</strong> [1]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2]
<strong>Output:</strong> [1,2]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定一个大小为 <em>n </em>的整数数组，找出其中所有出现超过 <code>⌊ n/3 ⌋</code> 次的元素。</p>

<p><strong>进阶：</strong>尝试设计时间复杂度为 O(n)、空间复杂度为 O(1)的算法解决此问题。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>[3,2,3]
<strong>输出：</strong>[3]</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [1]
<strong>输出：</strong>[1]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>[1,1,1,3,3,2,2,2]
<strong>输出：</strong>[1,2]</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 5 * 10<sup>4</sup></code></li>
	<li><code>-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup></code></li>
</ul>


## Note

哈希表做很简单 但复杂度不够



用摩尔投票法  摩尔投票法分为两个阶段：抵消阶段和计数阶段


## Solution

Language: **python3**  /  Runtime: 64 ms

```python3
class Solution:
    def majorityElement(self, nums: List[int]) -> List[int]:
        words={}
        n=len(nums)
        s=[]
        for num in nums:
            words[num]=words.get(num,0)+1
            if words[num]>n//3 and num not in s:
                s.append(num)
        print(words)
        return s

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/majority-element-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/majority-element-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/majority-element-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/majority-element-ii/)

[回到目录](../README.md)