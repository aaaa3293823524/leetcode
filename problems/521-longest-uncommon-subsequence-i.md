# 521. longest-uncommon-subsequence-i | 最长特殊序列 Ⅰ

## Question description

<!--If you want to use the English description, use <p>Given two strings <code>a</code> and <code>b</code>, return <em>the length of the <strong>longest uncommon subsequence</strong> between </em><code>a</code> <em>and</em> <code>b</code>. If the longest uncommon subsequence does not exist, return <code>-1</code>.</p>

<p>An <strong>uncommon subsequence</strong> between two strings is a string that is a <strong>subsequence of one but not the other</strong>.</p>

<p>A <strong>subsequence</strong> of a string <code>s</code> is a string that can be obtained after deleting any number of characters from <code>s</code>.</p>

<ul>
	<li>For example, <code>&quot;abc&quot;</code> is a subsequence of <code>&quot;aebdc&quot;</code> because you can delete the underlined characters in <code>&quot;a<u>e</u>b<u>d</u>c&quot;</code> to get <code>&quot;abc&quot;</code>. Other subsequences of <code>&quot;aebdc&quot;</code> include <code>&quot;aebdc&quot;</code>, <code>&quot;aeb&quot;</code>, and <code>&quot;&quot;</code> (empty string).</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;aba&quot;, b = &quot;cdc&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> One longest uncommon subsequence is &quot;aba&quot; because &quot;aba&quot; is a subsequence of &quot;aba&quot; but not &quot;cdc&quot;.
Note that &quot;cdc&quot; is also a longest uncommon subsequence.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;aaa&quot;, b = &quot;bbb&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong>&nbsp;The longest uncommon subsequences are &quot;aaa&quot; and &quot;bbb&quot;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;aaa&quot;, b = &quot;aaa&quot;
<strong>Output:</strong> -1
<strong>Explanation:</strong>&nbsp;Every subsequence of string a is also a subsequence of string b. Similarly, every subsequence of string b is also a subsequence of string a.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= a.length, b.length &lt;= 100</code></li>
	<li><code>a</code> and <code>b</code> consist of lower-case English letters.</li>
</ul>
 instead-->
<p>给你两个字符串，请你从这两个字符串中找出最长的特殊序列。</p>

<p>「最长特殊序列」定义如下：该序列为某字符串独有的最长子序列（即不能是其他字符串的子序列）。</p>

<p><strong>子序列</strong> 可以通过删去字符串中的某些字符实现，但不能改变剩余字符的相对顺序。空序列为所有字符串的子序列，任何字符串为其自身的子序列。</p>

<p>输入为两个字符串，输出最长特殊序列的长度。如果不存在，则返回 -1。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入:</strong> &quot;aba&quot;, &quot;cdc&quot;
<strong>输出:</strong> 3
<strong>解释:</strong> 最长特殊序列可为 &quot;aba&quot; (或 &quot;cdc&quot;)，两者均为自身的子序列且不是对方的子序列。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>a = &quot;aaa&quot;, b = &quot;bbb&quot;
<strong>输出：</strong>3
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>a = &quot;aaa&quot;, b = &quot;aaa&quot;
<strong>输出：</strong>-1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>两个字符串长度均处于区间&nbsp;<code>[1 - 100]</code> 。</li>
	<li>字符串中的字符仅含有&nbsp;<code>&#39;a&#39;~&#39;z&#39;</code> 。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int findLUSlength(String a, String b) {
        return a.equals(b)?-1:Math.max(a.length(),b.length());
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-uncommon-subsequence-i/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-uncommon-subsequence-i/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-uncommon-subsequence-i/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-uncommon-subsequence-i/)

[回到目录](../README.md)