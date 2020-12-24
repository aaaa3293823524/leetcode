# 172. factorial-trailing-zeroes | 阶乘后的零

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>n</code>, return <em>the number of trailing zeroes in <code>n!</code></em>.</p>

<p><b>Follow up: </b>Could you write a&nbsp;solution that works in logarithmic time complexity?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 3
<strong>Output:</strong> 0
<strong>Explanation:</strong>&nbsp;3! = 6, no trailing zero.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 5
<strong>Output:</strong> 1
<strong>Explanation:</strong>&nbsp;5! = 120, one trailing zero.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给定一个整数 <em>n</em>，返回 <em>n</em>! 结果尾数中零的数量。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong> 0
<strong>解释:</strong>&nbsp;3! = 6, 尾数中没有零。</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> 5
<strong>输出:</strong> 1
<strong>解释:</strong>&nbsp;5! = 120, 尾数中有 1 个零.</pre>

<p><strong>说明: </strong>你算法的时间复杂度应为&nbsp;<em>O</em>(log&nbsp;<em>n</em>)<em>&nbsp;</em>。</p>




## Solution

Language: **python3**  /  Runtime: 48 ms

```python3
class Solution:
    def trailingZeroes(self, n: int) -> int:
        p = 0
        while n >= 5:
            n = n // 5
            p += n
        return p
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/factorial-trailing-zeroes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/factorial-trailing-zeroes/description/)

Solution: [LeetCode](https://leetcode.com/articles/factorial-trailing-zeroes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/factorial-trailing-zeroes/)

[回到目录](../README.md)