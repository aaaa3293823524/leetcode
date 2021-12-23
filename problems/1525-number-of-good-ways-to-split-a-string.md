# 1525. number-of-good-ways-to-split-a-string | 字符串的好分割数目

## Question description

<!--If you want to use the English description, use <p>You are given a string <code>s</code>, a&nbsp;split is called <em>good</em>&nbsp;if you can split&nbsp;<code>s</code> into 2&nbsp;non-empty strings <code>p</code> and <code>q</code> where its concatenation is equal to <code>s</code> and the number of distinct letters in <code>p</code> and <code>q</code> are the same.</p>

<p>Return the number of <em>good</em> splits you can make in <code>s</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aacaba&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are 5 ways to split <code>&quot;aacaba&quot;</code> and 2 of them are good. 
(&quot;a&quot;, &quot;acaba&quot;) Left string and right string contains 1 and 3 different letters respectively.
(&quot;aa&quot;, &quot;caba&quot;) Left string and right string contains 1 and 3 different letters respectively.
(&quot;aac&quot;, &quot;aba&quot;) Left string and right string contains 2 and 2 different letters respectively (good split).
(&quot;aaca&quot;, &quot;ba&quot;) Left string and right string contains 2 and 2 different letters respectively (good split).
(&quot;aacab&quot;, &quot;a&quot;) Left string and right string contains 3 and 1 different letters respectively.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcd&quot;
<strong>Output:</strong> 1
<strong>Explanation: </strong>Split the string as follows (&quot;ab&quot;, &quot;cd&quot;).
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aaaaa&quot;
<strong>Output:</strong> 4
<strong>Explanation: </strong>All possible splits are good.</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;acbadbaada&quot;
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>s</code> contains only lowercase English letters.</li>
	<li><code>1 &lt;= s.length &lt;= 10^5</code></li>
</ul> instead-->
<p>给你一个字符串&nbsp;<code>s</code>&nbsp;，一个分割被称为 「好分割」&nbsp;当它满足：将&nbsp;<code>s</code>&nbsp;分割成 2 个字符串&nbsp;<code>p</code> 和&nbsp;<code>q</code>&nbsp;，它们连接起来等于&nbsp;<code>s</code>&nbsp;且 <code>p</code>&nbsp;和 <code>q</code>&nbsp;中不同字符的数目相同。</p>

<p>请你返回 <code>s</code>&nbsp;中好分割的数目。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;aacaba&quot;
<strong>输出：</strong>2
<strong>解释：</strong>总共有 5 种分割字符串 <code>&quot;aacaba&quot;</code> 的方法，其中 2 种是好分割。
(&quot;a&quot;, &quot;acaba&quot;) 左边字符串和右边字符串分别包含 1 个和 3 个不同的字符。
(&quot;aa&quot;, &quot;caba&quot;) 左边字符串和右边字符串分别包含 1 个和 3 个不同的字符。
(&quot;aac&quot;, &quot;aba&quot;) 左边字符串和右边字符串分别包含 2 个和 2 个不同的字符。这是一个好分割。
(&quot;aaca&quot;, &quot;ba&quot;) 左边字符串和右边字符串分别包含 2 个和 2 个不同的字符。这是一个好分割。
(&quot;aacab&quot;, &quot;a&quot;) 左边字符串和右边字符串分别包含 3 个和 1 个不同的字符。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = &quot;abcd&quot;
<strong>输出：</strong>1
<strong>解释：</strong>好分割为将字符串分割成 (&quot;ab&quot;, &quot;cd&quot;) 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = &quot;aaaaa&quot;
<strong>输出：</strong>4
<strong>解释：</strong>所有分割都是好分割。</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>s = &quot;acbadbaada&quot;
<strong>输出：</strong>2
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>s</code>&nbsp;只包含小写英文字母。</li>
	<li><code>1 &lt;= s.length &lt;= 10^5</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public int numSplits(String s) {
        int n = s.length();
        int[] left = new int[n + 2];
        int[] right = new int[n + 2];
        boolean[] recLeft = new boolean[26];
        boolean[] recRight = new boolean[26];
        for (int i = 1; i <= n; i++) {
            int c = s.charAt(i - 1) - 'a';
            if (recLeft[c]) {
                left[i] = left[i - 1];
            } else {
                recLeft[c] = true;;
                left[i] = left[i - 1] + 1;
            }
        }
        for (int i = n; i > 0; i--) {
            int c = s.charAt(i - 1) - 'a';
            if (recRight[c]) {
                right[i] = right[i + 1];
            } else {
                recRight[c] = true;
                right[i] = right[i + 1] + 1;
            }
        }
        int ret = 0;
        for (int i = 1; i < n; i++) {
            if (left[i] == right[i + 1]) {
                ret++;
            }
        }
        return ret;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-good-ways-to-split-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-good-ways-to-split-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-good-ways-to-split-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-good-ways-to-split-a-string/)

[回到目录](../README.md)