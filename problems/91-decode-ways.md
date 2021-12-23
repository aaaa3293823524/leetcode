# 91. decode-ways | 解码方法

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

<p>Given a string <code>s</code> containing only digits, return <em>the <strong>number</strong> of ways to <strong>decode</strong> it</em>.</p>

<p>The test cases are generated so that the answer fits in a <strong>32-bit</strong> integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;12&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> &quot;12&quot; could be decoded as &quot;AB&quot; (1 2) or &quot;L&quot; (12).
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;226&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> &quot;226&quot; could be decoded as &quot;BZ&quot; (2 26), &quot;VF&quot; (22 6), or &quot;BBF&quot; (2 2 6).
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;06&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> &quot;06&quot; cannot be mapped to &quot;F&quot; because of the leading zero (&quot;6&quot; is different from &quot;06&quot;).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s</code> contains only digits and may contain leading zero(s).</li>
</ul>
 instead-->
<p>一条包含字母 <code>A-Z</code> 的消息通过以下映射进行了 <strong>编码</strong> ：</p>

<pre>
'A' -> 1
'B' -> 2
...
'Z' -> 26
</pre>

<p>要 <strong>解码</strong> 已编码的消息，所有数字必须基于上述映射的方法，反向映射回字母（可能有多种方法）。例如，<code>"11106"</code> 可以映射为：</p>

<ul>
	<li><code>"AAJF"</code> ，将消息分组为 <code>(1 1 10 6)</code></li>
	<li><code>"KJF"</code> ，将消息分组为 <code>(11 10 6)</code></li>
</ul>

<p>注意，消息不能分组为  <code>(1 11 06)</code> ，因为 <code>"06"</code> 不能映射为 <code>"F"</code> ，这是由于 <code>"6"</code> 和 <code>"06"</code> 在映射中并不等价。</p>

<p>给你一个只含数字的 <strong>非空 </strong>字符串 <code>s</code> ，请计算并返回 <strong>解码</strong> 方法的 <strong>总数</strong> 。</p>

<p>题目数据保证答案肯定是一个 <strong>32 位</strong> 的整数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "12"
<strong>输出：</strong>2
<strong>解释：</strong>它可以解码为 "AB"（1 2）或者 "L"（12）。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "226"
<strong>输出：</strong>3
<strong>解释：</strong>它可以解码为 "BZ" (2 26), "VF" (22 6), 或者 "BBF" (2 2 6) 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "0"
<strong>输出：</strong>0
<strong>解释：</strong>没有字符映射到以 0 开头的数字。
含有 0 的有效映射是 'J' -> "10" 和 'T'-> "20" 。
由于没有字符，因此没有有效的方法对此进行解码，因为所有数字都需要映射。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>s = "06"
<strong>输出：</strong>0
<strong>解释：</strong>"06" 不能映射到 "F" ，因为字符串含有前导 0（<code>"6"</code> 和 <code>"06"</code> 在映射中并不等价）。</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 100</code></li>
	<li><code>s</code> 只包含数字，并且可能包含前导零。</li>
</ul>


## Note

动态规划



dp[i]表示 str[0...i]方法



最优子结构


## Solution

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:
    int numDecodings(string s) {
    if (s[0] == '0') return 0;
    int pre = 1, curr = 1;//dp[-1] = dp[0] = 1
    for (int i = 1; i < s.size(); i++) {
        int tmp = curr;
        if (s[i] == '0')
            if (s[i - 1] == '1' || s[i - 1] == '2') curr = pre;
            else return 0;
        else if (s[i - 1] == '1' || (s[i - 1] == '2' && s[i] >= '1' && s[i] <= '6'))
            curr = curr + pre;
        pre = tmp;
    }
    return curr;
}


};
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/decode-ways/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/decode-ways/description/)

Solution: [LeetCode](https://leetcode.com/articles/decode-ways/)  /  [LeetCode中国](https://leetcode-cn.com/articles/decode-ways/)

[回到目录](../README.md)