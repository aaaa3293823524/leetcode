# 639. decode-ways-ii | 解码方法 II

## Question description

<!--If you want to use the English description, use <p>A message containing letters from <code>A-Z</code> can be <strong>encoded</strong> into numbers using the following mapping:</p>

<pre>
&#39;A&#39; -&gt; &quot;1&quot;
&#39;B&#39; -&gt; &quot;2&quot;
...
&#39;Z&#39; -&gt; &quot;26&quot;
</pre>

<p>To <strong>decode</strong> an encoded message, all the digits must be grouped then mapped back into letters using the reverse of the mapping above (there may be multiple ways). For example, <code>&quot;11106&quot;</code> can be mapped into:</p>

<ul>
	<li><code>&quot;AAJF&quot;</code> with the grouping <code>(1 1 10 6)</code></li>
	<li><code>&quot;KJF&quot;</code> with the grouping <code>(11 10 6)</code></li>
</ul>

<p>Note that the grouping <code>(1 11 06)</code> is invalid because <code>&quot;06&quot;</code> cannot be mapped into <code>&#39;F&#39;</code> since <code>&quot;6&quot;</code> is different from <code>&quot;06&quot;</code>.</p>

<p><strong>In addition</strong> to the mapping above, an encoded message may contain the <code>&#39;*&#39;</code> character, which can represent any digit from <code>&#39;1&#39;</code> to <code>&#39;9&#39;</code> (<code>&#39;0&#39;</code> is excluded). For example, the encoded message <code>&quot;1*&quot;</code> may represent any of the encoded messages <code>&quot;11&quot;</code>, <code>&quot;12&quot;</code>, <code>&quot;13&quot;</code>, <code>&quot;14&quot;</code>, <code>&quot;15&quot;</code>, <code>&quot;16&quot;</code>, <code>&quot;17&quot;</code>, <code>&quot;18&quot;</code>, or <code>&quot;19&quot;</code>. Decoding <code>&quot;1*&quot;</code> is equivalent to decoding <strong>any</strong> of the encoded messages it can represent.</p>

<p>Given a string <code>s</code> consisting of digits and <code>&#39;*&#39;</code> characters, return <em>the <strong>number</strong> of ways to <strong>decode</strong> it</em>.</p>

<p>Since the answer may be very large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;*&quot;
<strong>Output:</strong> 9
<strong>Explanation:</strong> The encoded message can represent any of the encoded messages &quot;1&quot;, &quot;2&quot;, &quot;3&quot;, &quot;4&quot;, &quot;5&quot;, &quot;6&quot;, &quot;7&quot;, &quot;8&quot;, or &quot;9&quot;.
Each of these can be decoded to the strings &quot;A&quot;, &quot;B&quot;, &quot;C&quot;, &quot;D&quot;, &quot;E&quot;, &quot;F&quot;, &quot;G&quot;, &quot;H&quot;, and &quot;I&quot; respectively.
Hence, there are a total of 9 ways to decode &quot;*&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1*&quot;
<strong>Output:</strong> 18
<strong>Explanation:</strong> The encoded message can represent any of the encoded messages &quot;11&quot;, &quot;12&quot;, &quot;13&quot;, &quot;14&quot;, &quot;15&quot;, &quot;16&quot;, &quot;17&quot;, &quot;18&quot;, or &quot;19&quot;.
Each of these encoded messages have 2 ways to be decoded (e.g. &quot;11&quot; can be decoded to &quot;AA&quot; or &quot;K&quot;).
Hence, there are a total of 9 * 2 = 18 ways to decode &quot;1*&quot;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;2*&quot;
<strong>Output:</strong> 15
<strong>Explanation:</strong> The encoded message can represent any of the encoded messages &quot;21&quot;, &quot;22&quot;, &quot;23&quot;, &quot;24&quot;, &quot;25&quot;, &quot;26&quot;, &quot;27&quot;, &quot;28&quot;, or &quot;29&quot;.
&quot;21&quot;, &quot;22&quot;, &quot;23&quot;, &quot;24&quot;, &quot;25&quot;, and &quot;26&quot; have 2 ways of being decoded, but &quot;27&quot;, &quot;28&quot;, and &quot;29&quot; only have 1 way.
Hence, there are a total of (6 * 2) + (3 * 1) = 12 + 3 = 15 ways to decode &quot;2*&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is a digit or <code>&#39;*&#39;</code>.</li>
</ul>
 instead-->
<p>一条包含字母&nbsp;<code>A-Z</code> 的消息通过以下的方式进行了编码：</p>

<pre>
'A' -&gt; 1
'B' -&gt; 2
...
'Z' -&gt; 26
</pre>

<p>要 <strong>解码</strong> 一条已编码的消息，所有的数字都必须分组，然后按原来的编码方案反向映射回字母（可能存在多种方式）。例如，<code>"11106"</code> 可以映射为：</p>

<ul>
	<li><code>"AAJF"</code> 对应分组 <code>(1 1 10 6)</code></li>
	<li><code>"KJF"</code> 对应分组 <code>(11 10 6)</code></li>
</ul>

<p>注意，像 <code>(1 11 06)</code> 这样的分组是无效的，因为 <code>"06"</code> 不可以映射为 <code>'F'</code> ，因为 <code>"6"</code> 与 <code>"06"</code> 不同。</p>

<p><strong>除了</strong> 上面描述的数字字母映射方案，编码消息中可能包含 <code>'*'</code> 字符，可以表示从 <code>'1'</code> 到 <code>'9'</code> 的任一数字（不包括 <code>'0'</code>）。例如，编码字符串 <code>"1*"</code> 可以表示 <code>"11"</code>、<code>"12"</code>、<code>"13"</code>、<code>"14"</code>、<code>"15"</code>、<code>"16"</code>、<code>"17"</code>、<code>"18"</code> 或 <code>"19"</code> 中的任意一条消息。对 <code>"1*"</code> 进行解码，相当于解码该字符串可以表示的任何编码消息。</p>

<p>给你一个字符串 <code>s</code> ，由数字和 <code>'*'</code> 字符组成，返回 <strong>解码</strong> 该字符串的方法 <strong>数目</strong> 。</p>

<p>由于答案数目可能非常大，返回对 <code>10<sup>9</sup> + 7</code> <strong>取余</strong> 的结果。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "*"
<strong>输出：</strong>9
<strong>解释：</strong>这一条编码消息可以表示 "1"、"2"、"3"、"4"、"5"、"6"、"7"、"8" 或 "9" 中的任意一条。
可以分别解码成字符串 "A"、"B"、"C"、"D"、"E"、"F"、"G"、"H" 和 "I" 。
因此，"*" 总共有 9 种解码方法。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "1*"
<strong>输出：</strong>18
<strong>解释：</strong>这一条编码消息可以表示 "11"、"12"、"13"、"14"、"15"、"16"、"17"、"18" 或 "19" 中的任意一条。
每种消息都可以由 2 种方法解码（例如，"11" 可以解码成 "AA" 或 "K"）。
因此，"1*" 共有 9 * 2 = 18 种解码方法。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "2*"
<strong>输出：</strong>15
<strong>解释：</strong>这一条编码消息可以表示 "21"、"22"、"23"、"24"、"25"、"26"、"27"、"28" 或 "29" 中的任意一条。
"21"、"22"、"23"、"24"、"25" 和 "26" 由 2 种解码方法，但 "27"、"28" 和 "29" 仅有 1 种解码方法。
因此，"2*" 共有 (6 * 2) + (3 * 1) = 12 + 3 = 15 种解码方法。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> 是 <code>0 - 9</code> 中的一位数字或字符 <code>'*'</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 20 ms

```java
class Solution {
    static final int MOD = 1000000007;

    public int numDecodings(String s) {
        int n = s.length();
        // a = f[i-2], b = f[i-1], c = f[i]
        long a = 0, b = 1, c = 0;
        for (int i = 1; i <= n; ++i) {
            c = b * check1digit(s.charAt(i - 1)) % MOD;
            if (i > 1) {
                c = (c + a * check2digits(s.charAt(i - 2), s.charAt(i - 1))) % MOD;
            }
            a = b;
            b = c;
        }
        return (int) c;
    }

    public int check1digit(char ch) {
        if (ch == '0') {
            return 0;
        }
        return ch == '*' ? 9 : 1;
    }

    public int check2digits(char c0, char c1) {
        if (c0 == '*' && c1 == '*') {
            return 15;
        }
        if (c0 == '*') {
            return c1 <= '6' ? 2 : 1;
        }
        if (c1 == '*') {
            if (c0 == '1') {
                return 9;
            }
            if (c0 == '2') {
                return 6;
            }
            return 0;
        }
        return (c0 != '0' && (c0 - '0') * 10 + (c1 - '0') <= 26) ? 1 : 0;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/decode-ways-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/decode-ways-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/decode-ways-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/decode-ways-ii/)

[回到目录](../README.md)