# 926. flip-string-to-monotone-increasing | 将字符串翻转到单调递增

## Question description

<!--If you want to use the English description, use <p>A binary string is monotone increasing if it consists of some number of <code>0</code>&#39;s (possibly none), followed by some number of <code>1</code>&#39;s (also possibly none).</p>

<p>You are given a binary string <code>s</code>. You can flip <code>s[i]</code> changing it from <code>0</code> to <code>1</code> or from <code>1</code> to <code>0</code>.</p>

<p>Return <em>the minimum number of flips to make </em><code>s</code><em> monotone increasing</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;00110&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> We flip the last digit to get 00111.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;010110&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> We flip to get 011111, or alternatively 000111.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;00011000&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> We flip to get 00000000.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is either <code>&#39;0&#39;</code> or <code>&#39;1&#39;</code>.</li>
</ul>
 instead-->
<p>如果一个由 <code>'0'</code> 和 <code>'1'</code> 组成的字符串，是以一些 <code>'0'</code>（可能没有 <code>'0'</code>）后面跟着一些 <code>'1'</code>（也可能没有 <code>'1'</code>）的形式组成的，那么该字符串是<em>单调递增</em>的。</p>

<p>我们给出一个由字符 <code>'0'</code> 和 <code>'1'</code> 组成的字符串 <code>S</code>，我们可以将任何 <code>'0'</code> 翻转为 <code>'1'</code> 或者将 <code>'1'</code> 翻转为 <code>'0'</code>。</p>

<p>返回使 <code>S</code> 单调递增的最小翻转次数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>"00110"
<strong>输出：</strong>1
<strong>解释：</strong>我们翻转最后一位得到 00111.
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>"010110"
<strong>输出：</strong>2
<strong>解释：</strong>我们翻转得到 011111，或者是 000111。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>"00011000"
<strong>输出：</strong>2
<strong>解释：</strong>我们翻转得到 00000000。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= S.length <= 20000</code></li>
	<li><code>S</code> 中只包含字符 <code>'0'</code> 和 <code>'1'</code></li>
</ul>


## Note

动态规划



遍历字符串，对于字符串的每一个位置，当字符串翻转完毕之后，该位置只可能处于两种状态：0阶段或者1阶段。用zero记录令当前位置处于0阶段的花费，用one记录令当前位置处于1阶段的花费，因为0阶段要求前一位置必须处于0阶段，而1阶段允许前一位置处于0阶段或者1阶段，故状态转移公式如下：

zero[i]=zero[i-1]+cost_to_0(S[i])

one[i]=min(zero[i-1], one[i-1])+cost_to_1(S[i])






## Solution

Language: **python3**  /  Runtime: 76 ms

```python3
class Solution:
    def minFlipsMonoIncr(self, S: str) -> int:
        zero=one=0

        for char in S:
            zero, one=zero+int(char!='0'), min(zero, one)+int(char!='1')
        
        return min(zero, one)


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/flip-string-to-monotone-increasing/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/flip-string-to-monotone-increasing/description/)

Solution: [LeetCode](https://leetcode.com/articles/flip-string-to-monotone-increasing/)  /  [LeetCode中国](https://leetcode-cn.com/articles/flip-string-to-monotone-increasing/)

[回到目录](../README.md)