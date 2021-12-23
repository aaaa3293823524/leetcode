# 1573. number-of-ways-to-split-a-string | 分割字符串的方案数

## Question description

<!--If you want to use the English description, use <p>Given a binary string <code>s</code> (a string consisting only of &#39;0&#39;s and &#39;1&#39;s),&nbsp;we can split <code>s</code>&nbsp;into 3 <strong>non-empty</strong> strings s1, s2, s3 (s1+ s2+ s3 = s).</p>

<p>Return the number of ways <code>s</code> can be split such that the number of&nbsp;characters &#39;1&#39; is the same in s1, s2, and s3.</p>

<p>Since the answer&nbsp;may be too large,&nbsp;return it modulo&nbsp;10^9 + 7.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;10101&quot;
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are four ways to split s in 3 parts where each part contain the same number of letters &#39;1&#39;.
&quot;1|010|1&quot;
&quot;1|01|01&quot;
&quot;10|10|1&quot;
&quot;10|1|01&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1001&quot;
<strong>Output:</strong> 0
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;0000&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> There are three ways to split s in 3 parts.
&quot;0|0|00&quot;
&quot;0|00|0&quot;
&quot;00|0|0&quot;
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;100100010100110&quot;
<strong>Output:</strong> 12
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 10^5</code></li>
	<li><code>s[i]</code> is <code>&#39;0&#39;</code>&nbsp;or&nbsp;<code>&#39;1&#39;</code>.</li>
</ul>
 instead-->
<p>给你一个二进制串&nbsp;<code>s</code>&nbsp; （一个只包含 0 和 1 的字符串），我们可以将 <code>s</code>&nbsp;分割成 3 个 <strong>非空</strong>&nbsp;字符串 s1, s2, s3 （s1 + s2 + s3 = s）。</p>

<p>请你返回分割&nbsp;<code>s</code>&nbsp;的方案数，满足 s1，s2 和 s3 中字符 &#39;1&#39; 的数目相同。</p>

<p>由于答案可能很大，请将它对 10^9 + 7 取余后返回。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;10101&quot;
<strong>输出：</strong>4
<strong>解释：</strong>总共有 4 种方法将 s 分割成含有 &#39;1&#39; 数目相同的三个子字符串。
&quot;1|010|1&quot;
&quot;1|01|01&quot;
&quot;10|10|1&quot;
&quot;10|1|01&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = &quot;1001&quot;
<strong>输出：</strong>0
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = &quot;0000&quot;
<strong>输出：</strong>3
<strong>解释：</strong>总共有 3 种分割 s 的方法。
&quot;0|0|00&quot;
&quot;0|00|0&quot;
&quot;00|0|0&quot;
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>s = &quot;100100010100110&quot;
<strong>输出：</strong>12
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>s[i] == &#39;0&#39;</code>&nbsp;或者&nbsp;<code>s[i] == &#39;1&#39;</code></li>
	<li><code>3 &lt;= s.length &lt;= 10^5</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public int numWays(String s) {
        int len = s.length();
        int count_1 = 0;
        for (int i = 0; i < len; i++) {
            if (s.charAt(i) == '1') count_1++;
        }
        if (count_1 == 0){
            int n = len - 1;
            return (int)((1L * n * (n - 1) / 2) % 1000000007);
        }else if (count_1 % 3 != 0){
            return 0;
        }else{
            int k = count_1 / 3;    // 每一段包含1的个数
            int count = 0, m = 0, n = 0;    // count用来计数目前1的个数
            for (int i = 0; i < len; i++) {
                if (s.charAt(i) == '1'){
                    count++;
                    if (count == k) m = i;
                    if (count == k + 1) m = i - m;
                    if (count == k * 2) n = i;
                    if (count == k * 2 + 1){
                        n = i - n;
                        break;
                    }
                }
            }
            return (int)((1L * m * n) % 1000000007);
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-ways-to-split-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-ways-to-split-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-ways-to-split-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-ways-to-split-a-string/)

[回到目录](../README.md)