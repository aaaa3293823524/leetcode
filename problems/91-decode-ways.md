# 91. decode-ways | 解码方法

## Question description

<!--If you want to use the English description, use <p>A message containing letters from <code>A-Z</code> is being encoded to numbers using the following mapping:</p>

<pre>
&#39;A&#39; -&gt; 1
&#39;B&#39; -&gt; 2
...
&#39;Z&#39; -&gt; 26
</pre>

<p>Given a <strong>non-empty</strong> string containing only digits, determine the total number of ways to decode it.</p>

<p>The answer is guaranteed to fit in a <strong>32-bit</strong> integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;12&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> It could be decoded as &quot;AB&quot; (1 2) or &quot;L&quot; (12).
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;226&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> It could be decoded as &quot;BZ&quot; (2 26), &quot;VF&quot; (22 6), or &quot;BBF&quot; (2 2 6).
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;0&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> There is no character that is mapped to a number starting with &#39;0&#39;. We cannot ignore a zero when we face it while decoding. So, each &#39;0&#39; should be part of &quot;10&quot; --&gt; &#39;J&#39; or &quot;20&quot; --&gt; &#39;T&#39;.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1&quot;
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s</code> contains only digits and may contain leading zero(s).</li>
</ul>
 instead-->
<p>一条包含字母 <code>A-Z</code> 的消息通过以下方式进行了编码：</p>

<pre>
'A' -> 1
'B' -> 2
...
'Z' -> 26
</pre>

<p>给定一个只包含数字的<strong>非空</strong>字符串，请计算解码方法的总数。</p>

<p>题目数据保证答案肯定是一个 32 位的整数。</p>

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
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>s = "1"
<strong>输出：</strong>1
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>s = "2"
<strong>输出：</strong>1
</pre>

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