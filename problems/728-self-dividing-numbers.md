# 728. self-dividing-numbers | 自除数

## Question description

<!--If you want to use the English description, use <p>A <strong>self-dividing number</strong> is a number that is divisible by every digit it contains.</p>

<ul>
	<li>For example, <code>128</code> is <strong>a self-dividing number</strong> because <code>128 % 1 == 0</code>, <code>128 % 2 == 0</code>, and <code>128 % 8 == 0</code>.</li>
</ul>

<p>A <strong>self-dividing number</strong> is not allowed to contain the digit zero.</p>

<p>Given two integers <code>left</code> and <code>right</code>, return <em>a list of all the <strong>self-dividing numbers</strong> in the range</em> <code>[left, right]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> left = 1, right = 22
<strong>Output:</strong> [1,2,3,4,5,6,7,8,9,11,12,15,22]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> left = 47, right = 85
<strong>Output:</strong> [48,55,66,77]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= left &lt;= right &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p><em>自除数&nbsp;</em>是指可以被它包含的每一位数除尽的数。</p>

<p>例如，128 是一个自除数，因为&nbsp;<code>128 % 1 == 0</code>，<code>128 % 2 == 0</code>，<code>128 % 8 == 0</code>。</p>

<p>还有，自除数不允许包含 0 。</p>

<p>给定上边界和下边界数字，输出一个列表，列表的元素是边界（含边界）内所有的自除数。</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong> 
上边界left = 1, 下边界right = 22
<strong>输出：</strong> [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
</pre>

<p><strong>注意：</strong></p>

<ul>
	<li>每个输入参数的边界满足&nbsp;<code>1 &lt;= left &lt;= right &lt;= 10000</code>。</li>
</ul>




## Solution

Language: **python3**  /  Runtime: 196 ms

```python3
class Solution:
    def selfDividingNumbers(self, left: int, right: int) -> List[int]:
        return [n for n in range(left, right + 1) if \
               '0' not in str(n) and all([n % int(b) == 0 for b in str(n)])]


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/self-dividing-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/self-dividing-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/self-dividing-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/self-dividing-numbers/)

[回到目录](../README.md)