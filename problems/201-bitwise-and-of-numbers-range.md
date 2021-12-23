# 201. bitwise-and-of-numbers-range | 数字范围按位与

## Question description

<!--If you want to use the English description, use <p>Given two integers <code>left</code> and <code>right</code> that represent the range <code>[left, right]</code>, return <em>the bitwise AND of all numbers in this range, inclusive</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> left = 5, right = 7
<strong>Output:</strong> 4
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> left = 0, right = 0
<strong>Output:</strong> 0
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> left = 1, right = 2147483647
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= left &lt;= right &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给你两个整数 <code>left</code> 和 <code>right</code> ，表示区间 <code>[left, right]</code> ，返回此区间内所有数字 <strong>按位与</strong> 的结果（包含 <code>left</code> 、<code>right</code> 端点）。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>left = 5, right = 7
<strong>输出：</strong>4
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>left = 0, right = 0
<strong>输出：</strong>0
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>left = 1, right = 2147483647
<strong>输出：</strong>0
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= left <= right <= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 7 ms

```java
class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        int shift = 0;
        // 找到公共前缀
        while (m < n) {
            m >>= 1;
            n >>= 1;
            ++shift;
        }
        return m << shift;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/bitwise-and-of-numbers-range/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/bitwise-and-of-numbers-range/description/)

Solution: [LeetCode](https://leetcode.com/articles/bitwise-and-of-numbers-range/)  /  [LeetCode中国](https://leetcode-cn.com/articles/bitwise-and-of-numbers-range/)

[回到目录](../README.md)