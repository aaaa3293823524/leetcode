# 263. ugly-number | 丑数

## Question description

<!--If you want to use the English description, use <p>Write a program to check whether a given number is an ugly number.</p>

<p>Ugly numbers are <strong>positive numbers</strong> whose prime factors only include <code>2, 3, 5</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 6
<strong>Output:</strong> true
<strong>Explanation: </strong>6 = 2 &times;&nbsp;3</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 8
<strong>Output:</strong> true
<strong>Explanation: </strong>8 = 2 &times; 2 &times;&nbsp;2
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> 14
<strong>Output:</strong> false 
<strong>Explanation: </strong><code>14</code> is not ugly since it includes another prime factor <code>7</code>.
</pre>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1</code> is typically treated as an ugly number.</li>
	<li>Input is within the 32-bit signed integer range:&nbsp;[&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1].</li>
</ol> instead-->
<p>编写一个程序判断给定的数是否为丑数。</p>

<p>丑数就是只包含质因数&nbsp;<code>2, 3, 5</code>&nbsp;的<strong>正整数</strong>。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 6
<strong>输出:</strong> true
<strong>解释: </strong>6 = 2 &times;&nbsp;3</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> 8
<strong>输出:</strong> true
<strong>解释: </strong>8 = 2 &times; 2 &times;&nbsp;2
</pre>

<p><strong>示例&nbsp;3:</strong></p>

<pre><strong>输入:</strong> 14
<strong>输出:</strong> false 
<strong>解释: </strong><code>14</code> 不是丑数，因为它包含了另外一个质因数&nbsp;<code>7</code>。</pre>

<p><strong>说明：</strong></p>

<ol>
	<li><code>1</code>&nbsp;是丑数。</li>
	<li>输入不会超过 32 位有符号整数的范围:&nbsp;[&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1]。</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 68 ms

```python3
class Solution:
    def isUgly(self, num: int) -> bool:
        if num == 0: return False
        if num == 1:return True
        if num % 2 == 0: return self.isUgly(num // 2)
        if num % 3 == 0: return self.isUgly(num // 3)
        if num % 5 == 0: return self.isUgly(num // 5)
        return False


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/ugly-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ugly-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/ugly-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/ugly-number/)

[回到目录](../README.md)