# 1653. minimum-deletions-to-make-string-balanced | 使字符串平衡的最少删除次数

## Question description

<!--If you want to use the English description, use <p>You are given a string <code>s</code> consisting only of characters <code>&#39;a&#39;</code> and <code>&#39;b&#39;</code>​​​​.</p>

<p>You can delete any number of characters in <code>s</code> to make <code>s</code> <strong>balanced</strong>. <code>s</code> is <strong>balanced</strong> if there is no pair of indices <code>(i,j)</code> such that <code>i &lt; j</code> and <code>s[i] = &#39;b&#39;</code> and <code>s[j]= &#39;a&#39;</code>.</p>

<p>Return <em>the <strong>minimum</strong> number of deletions needed to make </em><code>s</code><em> <strong>balanced</strong></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aababbab&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> You can either:
Delete the characters at 0-indexed positions 2 and 6 (&quot;aa<u>b</u>abb<u>a</u>b&quot; -&gt; &quot;aaabbb&quot;), or
Delete the characters at 0-indexed positions 3 and 6 (&quot;aab<u>a</u>bb<u>a</u>b&quot; -&gt; &quot;aabbbb&quot;).
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bbaaaaabb&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> The only solution is to delete the first two characters.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is&nbsp;<code>&#39;a&#39;</code> or <code>&#39;b&#39;</code>​​.</li>
</ul>
 instead-->
<p>给你一个字符串 <code>s</code> ，它仅包含字符 <code>'a'</code> 和 <code>'b'</code>​​​​ 。</p>

<p>你可以删除 <code>s</code> 中任意数目的字符，使得 <code>s</code> <strong>平衡</strong> 。我们称 <code>s</code> <strong>平衡的</strong> 当不存在下标对 <code>(i,j)</code> 满足 <code>i < j</code> 且 <code>s[i] = 'b'</code> 同时 <code>s[j]= 'a'</code> 。</p>

<p>请你返回使 <code>s</code> <strong>平衡</strong> 的 <strong>最少</strong> 删除次数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>s = "aababbab"
<b>输出：</b>2
<b>解释：</b>你可以选择以下任意一种方案：
下标从 0 开始，删除第 2 和第 6 个字符（"aa<strong>b</strong>abb<strong>a</strong>b" -> "aaabbb"），
下标从 0 开始，删除第 3 和第 6 个字符（"aab<strong>a</strong>bb<strong>a</strong>b" -> "aabbbb"）。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>s = "bbaaaaabb"
<b>输出：</b>2
<b>解释：</b>唯一的最优解是删除最前面两个字符。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> 要么是 <code>'a'</code> 要么是 <code>'b'</code>​<strong> </strong>。​</li>
</ul>




## Solution

Language: **java**  /  Runtime: 33 ms

```java
class Solution {
  public int minimumDeletions(String s) {
    s = " " + s;
    int n = s.length();
    int[] a = new int[n], b = new int[n];
    for (int i = 1; i < n; i++) {
      char c = s.charAt(i);
      if (c == 'a') {
        a[i] = a[i - 1];
        b[i] = b[i - 1] + 1;
      } else {
        b[i] = Math.min(b[i - 1], a[i - 1]);
        a[i] = a[i - 1] + 1;
      }
    }
    return Math.min(a[n - 1], b[n - 1]);
  }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-deletions-to-make-string-balanced/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-deletions-to-make-string-balanced/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-deletions-to-make-string-balanced/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-deletions-to-make-string-balanced/)

[回到目录](../README.md)