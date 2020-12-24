# 908. smallest-range-i | 最小差值 I

## Question description

<!--If you want to use the English description, use <p>Given an array <code>A</code> of integers, for each integer <code>A[i]</code> we may choose any <code>x</code> with <code>-K &lt;= x &lt;= K</code>, and add <code>x</code> to <code>A[i]</code>.</p>

<p>After this process, we have some array <code>B</code>.</p>

<p>Return the smallest possible difference between the maximum value of <code>B</code>&nbsp;and the minimum value of <code>B</code>.</p>

<p>&nbsp;</p>

<ol>
</ol>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-1-1">[1]</span>, K = <span id="example-input-1-2">0</span>
<strong>Output: </strong><span id="example-output-1">0
<strong>Explanation</strong>: B = [1]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-2-1">[0,10]</span>, K = <span id="example-input-2-2">2</span>
<strong>Output: </strong><span id="example-output-2">6
</span><span id="example-output-1"><strong>Explanation</strong>: B = [2,8]</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>A = <span id="example-input-3-1">[1,3,6]</span>, K = <span id="example-input-3-2">3</span>
<strong>Output: </strong><span id="example-output-3">0
</span><span id="example-output-1"><strong>Explanation</strong>: B = [3,3,3] or B = [4,4,4]</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 10000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 10000</code></li>
	<li><code>0 &lt;= K &lt;= 10000</code></li>
</ol>
</div>
</div>
</div> instead-->
<p>给你一个整数数组 <code>A</code>，请你给数组中的每个元素 <code>A[i]</code> 都加上一个任意数字 <code>x</code> （<code>-K &lt;= x &lt;= K</code>），从而得到一个新数组 <code>B</code> 。</p>

<p>返回数组 <code>B</code> 的最大值和最小值之间可能存在的最小差值。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>A = [1], K = 0
<strong>输出：</strong>0
<strong>解释：</strong>B = [1]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = [0,10], K = 2
<strong>输出：</strong>6
<strong>解释：</strong>B = [2,8]
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>A = [1,3,6], K = 3
<strong>输出：</strong>0
<strong>解释：</strong>B = [3,3,3] 或 B = [4,4,4]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 10000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 10000</code></li>
	<li><code>0 &lt;= K &lt;= 10000</code></li>
</ol>




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