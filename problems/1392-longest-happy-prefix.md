# 1392. longest-happy-prefix | 最长快乐前缀

## Question description

<!--If you want to use the English description, use <p>A string is called a <strong>happy prefix</strong> if is a <strong>non-empty</strong> prefix which is also a suffix (excluding itself).</p>

<p>Given a string <code>s</code>, return <em>the <strong>longest happy prefix</strong> of</em> <code>s</code>. Return an empty string <code>&quot;&quot;</code> if no such prefix exists.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;level&quot;
<strong>Output:</strong> &quot;l&quot;
<strong>Explanation:</strong> s contains 4 prefix excluding itself (&quot;l&quot;, &quot;le&quot;, &quot;lev&quot;, &quot;leve&quot;), and suffix (&quot;l&quot;, &quot;el&quot;, &quot;vel&quot;, &quot;evel&quot;). The largest prefix which is also suffix is given by &quot;l&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ababab&quot;
<strong>Output:</strong> &quot;abab&quot;
<strong>Explanation:</strong> &quot;abab&quot; is the largest prefix which is also suffix. They can overlap in the original string.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;leetcodeleet&quot;
<strong>Output:</strong> &quot;leet&quot;
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;a&quot;
<strong>Output:</strong> &quot;&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> contains only lowercase English letters.</li>
</ul>
 instead-->
<p>「快乐前缀」是在原字符串中既是&nbsp;<strong>非空</strong> 前缀也是后缀（不包括原字符串自身）的字符串。</p>

<p>给你一个字符串 <code>s</code>，请你返回它的 <strong>最长快乐前缀</strong>。</p>

<p>如果不存在满足题意的前缀，则返回一个空字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;level&quot;
<strong>输出：</strong>&quot;l&quot;
<strong>解释：</strong>不包括 s 自己，一共有 4 个前缀（&quot;l&quot;, &quot;le&quot;, &quot;lev&quot;, &quot;leve&quot;）和 4 个后缀（&quot;l&quot;, &quot;el&quot;, &quot;vel&quot;, &quot;evel&quot;）。最长的既是前缀也是后缀的字符串是 &quot;l&quot; 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = &quot;ababab&quot;
<strong>输出：</strong>&quot;abab&quot;
<strong>解释：</strong>&quot;abab&quot; 是最长的既是前缀也是后缀的字符串。题目允许前后缀在原字符串中重叠。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = &quot;leetcodeleet&quot;
<strong>输出：</strong>&quot;leet&quot;
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>s = &quot;a&quot;
<strong>输出：</strong>&quot;&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10^5</code></li>
	<li><code>s</code> 只含有小写英文字母</li>
</ul>




## Solution

Language: **java**  /  Runtime: 15 ms

```java
class Solution {
    public String longestPrefix(String s) {
        int n = s.length();
        long prefix = 0, suffix = 0;
        long base = 31, mod = 1000000007, mul = 1;
        int happy = 0;
        for (int i = 1; i < n; ++i) {
            prefix = (prefix * base + (s.charAt(i - 1) - 'a')) % mod;
            suffix = (suffix + (s.charAt(n - i) - 'a') * mul) % mod;
            if (prefix == suffix) {
                happy = i;
            }
            mul = mul * base % mod;
        }
        return s.substring(0, happy);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-happy-prefix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-happy-prefix/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-happy-prefix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-happy-prefix/)

[回到目录](../README.md)