# 908. smallest-range-i | 最小差值 I

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>nums</code> and an integer <code>k</code>.</p>

<p>In one operation, you can choose any index <code>i</code> where <code>0 &lt;= i &lt; nums.length</code> and change <code>nums[i]</code> to <code>nums[i] + x</code> where <code>x</code> is an integer from the range <code>[-k, k]</code>. You can apply this operation <strong>at most once</strong> for each index <code>i</code>.</p>

<p>The <strong>score</strong> of <code>nums</code> is the difference between the maximum and minimum elements in <code>nums</code>.</p>

<p>Return <em>the minimum <strong>score</strong> of </em><code>nums</code><em> after applying the mentioned operation at most once for each index in it</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1], k = 0
<strong>Output:</strong> 0
<strong>Explanation:</strong> The score is max(nums) - min(nums) = 1 - 1 = 0.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,10], k = 2
<strong>Output:</strong> 6
<strong>Explanation:</strong> Change nums to be [2, 8]. The score is max(nums) - min(nums) = 8 - 2 = 6.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,3,6], k = 3
<strong>Output:</strong> 0
<strong>Explanation:</strong> Change nums to be [4, 4, 4]. The score is max(nums) - min(nums) = 4 - 4 = 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= k &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>nums</code>，请你给数组中的每个元素 <code>nums[i]</code> 都加上一个任意数字 <code>x</code> （<code>-k <= x <= k</code>），从而得到一个新数组 <code>result</code> 。</p>

<p>返回数组 <code>result</code> 的最大值和最小值之间可能存在的最小差值。</p>

<p> </p>

<ol>
</ol>

<ol>
</ol>

<div>
<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = <span id="example-input-1-1">[1]</span>, k = <span id="example-input-1-2">0</span>
<strong>输出：</strong><span id="example-output-1">0
<strong>解释：</strong>result = [1]</span>
</pre>

<div>
<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = <span id="example-input-2-1">[0,10]</span>, k = <span id="example-input-2-2">2</span>
<strong>输出：</strong><span id="example-output-2">6
</span><span id="example-output-1"><strong>解释：</strong></span><span>result = [2,8]</span>
</pre>

<div>
<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = <span id="example-input-3-1">[1,3,6]</span>, k = <span id="example-input-3-2">3</span>
<strong>输出：</strong><span id="example-output-3">0
</span><span id="example-output-1"><strong>解释：</strong></span><span>result = [3,3,3] or result = [4,4,4]</span>
</pre>
</div>
</div>
</div>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 10000</code></li>
	<li><code>0 <= nums[i] <= 10000</code></li>
	<li><code>0 <= k <= 10000</code></li>
</ul>




## Solution

Language: **python3**  /  Runtime: 184 ms

```python3
class Solution:
    def smallestRangeI(self, A: List[int], K: int) -> int:
        A.sort()
        if A[0]+K >=A[-1]-K:
            return 0
        else:
            return A[-1]-A[0]-2*K
        #return (A[0]+K >=A[-1]-K)?0:(A[-1]-A[0]-2*K)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/smallest-range-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/smallest-range-i/description/)

Solution: [LeetCode](https://leetcode.com/articles/smallest-range-i/)  /  [LeetCode中国](https://leetcode-cn.com/articles/smallest-range-i/)

[回到目录](../README.md)