﻿# 1639. number-of-ways-to-form-a-target-string-given-a-dictionary | 通过给定词典构造目标字符串的方案数

## Question description

<!--If you want to use the English description, use <p>You are given a list of strings of the <strong>same length</strong> <code>words</code> and a string <code>target</code>.</p>

<p>Your task is to form <code>target</code> using the given <code>words</code> under the following rules:</p>

<ul>
	<li><code>target</code> should be formed from left to right.</li>
	<li>To form the <code>i<sup>th</sup></code> character (<strong>0-indexed</strong>) of <code>target</code>, you can choose the <code>k<sup>th</sup></code> character of the <code>j<sup>th</sup></code> string in <code>words</code> if <code>target[i] = words[j][k]</code>.</li>
	<li>Once you use the <code>k<sup>th</sup></code> character of the <code>j<sup>th</sup></code> string of <code>words</code>, you <strong>can no longer</strong> use the <code>x<sup>th</sup></code> character of any string in <code>words</code> where <code>x &lt;= k</code>. In other words, all characters to the left of or at index <code>k</code> become unusuable for every string.</li>
	<li>Repeat the process until you form the string <code>target</code>.</li>
</ul>

<p><strong>Notice</strong>&nbsp;that you can use <strong>multiple characters</strong> from the <strong>same string</strong> in <code>words</code> provided the conditions above are met.</p>

<p>Return <em>the number of ways to form <code>target</code> from <code>words</code></em>. Since the answer may be too large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;acca&quot;,&quot;bbbb&quot;,&quot;caca&quot;], target = &quot;aba&quot;
<strong>Output:</strong> 6
<strong>Explanation:</strong> There are 6 ways to form target.
&quot;aba&quot; -&gt; index 0 (&quot;<u>a</u>cca&quot;), index 1 (&quot;b<u>b</u>bb&quot;), index 3 (&quot;cac<u>a</u>&quot;)
&quot;aba&quot; -&gt; index 0 (&quot;<u>a</u>cca&quot;), index 2 (&quot;bb<u>b</u>b&quot;), index 3 (&quot;cac<u>a</u>&quot;)
&quot;aba&quot; -&gt; index 0 (&quot;<u>a</u>cca&quot;), index 1 (&quot;b<u>b</u>bb&quot;), index 3 (&quot;acc<u>a</u>&quot;)
&quot;aba&quot; -&gt; index 0 (&quot;<u>a</u>cca&quot;), index 2 (&quot;bb<u>b</u>b&quot;), index 3 (&quot;acc<u>a</u>&quot;)
&quot;aba&quot; -&gt; index 1 (&quot;c<u>a</u>ca&quot;), index 2 (&quot;bb<u>b</u>b&quot;), index 3 (&quot;acc<u>a</u>&quot;)
&quot;aba&quot; -&gt; index 1 (&quot;c<u>a</u>ca&quot;), index 2 (&quot;bb<u>b</u>b&quot;), index 3 (&quot;cac<u>a</u>&quot;)
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;abba&quot;,&quot;baab&quot;], target = &quot;bab&quot;
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are 4 ways to form target.
&quot;bab&quot; -&gt; index 0 (&quot;<u>b</u>aab&quot;), index 1 (&quot;b<u>a</u>ab&quot;), index 2 (&quot;ab<u>b</u>a&quot;)
&quot;bab&quot; -&gt; index 0 (&quot;<u>b</u>aab&quot;), index 1 (&quot;b<u>a</u>ab&quot;), index 3 (&quot;baa<u>b</u>&quot;)
&quot;bab&quot; -&gt; index 0 (&quot;<u>b</u>aab&quot;), index 2 (&quot;ba<u>a</u>b&quot;), index 3 (&quot;baa<u>b</u>&quot;)
&quot;bab&quot; -&gt; index 1 (&quot;a<u>b</u>ba&quot;), index 2 (&quot;ba<u>a</u>b&quot;), index 3 (&quot;baa<u>b</u>&quot;)
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;abcd&quot;], target = &quot;abcd&quot;
<strong>Output:</strong> 1
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> words = [&quot;abab&quot;,&quot;baba&quot;,&quot;abba&quot;,&quot;baab&quot;], target = &quot;abba&quot;
<strong>Output:</strong> 16
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 1000</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 1000</code></li>
	<li>All strings in <code>words</code> have the same length.</li>
	<li><code>1 &lt;= target.length &lt;= 1000</code></li>
	<li><code>words[i]</code> and <code>target</code> contain only lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个字符串列表 <code>words</code> 和一个目标字符串 <code>target</code> 。<code>words</code> 中所有字符串都 <strong>长度相同</strong>  。</p>

<p>你的目标是使用给定的 <code>words</code> 字符串列表按照下述规则构造 <code>target</code> ：</p>

<ul>
	<li>从左到右依次构造 <code>target</code> 的每一个字符。</li>
	<li>为了得到 <code>target</code> 第 <code>i</code> 个字符（下标从 <strong>0</strong> 开始），当 <code>target[i] = words[j][k]</code> 时，你可以使用 <code>words</code> 列表中第 <code>j</code> 个字符串的第 <code>k</code> 个字符。</li>
	<li>一旦你使用了 <code>words</code> 中第 <code>j</code> 个字符串的第 <code>k</code> 个字符，你不能再使用 <code>words</code> 字符串列表中任意单词的第 <code>x</code> 个字符（<code>x <= k</code>）。也就是说，所有单词下标小于等于 <code>k</code> 的字符都不能再被使用。</li>
	<li>请你重复此过程直到得到目标字符串 <code>target</code> 。</li>
</ul>

<p><strong>请注意</strong>， 在构造目标字符串的过程中，你可以按照上述规定使用 <code>words</code> 列表中 <strong>同一个字符串</strong> 的 <strong>多个字符</strong> 。</p>

<p>请你返回使用 <code>words</code> 构造 <code>target</code> 的方案数。由于答案可能会很大，请对 <code>10<sup>9</sup> + 7</code> <strong>取余</strong> 后返回。</p>

<p>（译者注：此题目求的是有多少个不同的 <code>k</code> 序列，详情请见示例。）</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>words = ["acca","bbbb","caca"], target = "aba"
<b>输出：</b>6
<b>解释：</b>总共有 6 种方法构造目标串。
"aba" -> 下标为 0 ("<strong>a</strong>cca")，下标为 1 ("b<strong>b</strong>bb")，下标为 3 ("cac<strong>a</strong>")
"aba" -> 下标为 0 ("<strong>a</strong>cca")，下标为 2 ("bb<strong>b</strong>b")，下标为 3 ("cac<strong>a</strong>")
"aba" -> 下标为 0 ("<strong>a</strong>cca")，下标为 1 ("b<strong>b</strong>bb")，下标为 3 ("acc<strong>a</strong>")
"aba" -> 下标为 0 ("<strong>a</strong>cca")，下标为 2 ("bb<strong>b</strong>b")，下标为 3 ("acc<strong>a</strong>")
"aba" -> 下标为 1 ("c<strong>a</strong>ca")，下标为 2 ("bb<strong>b</strong>b")，下标为 3 ("acc<strong>a</strong>")
"aba" -> 下标为 1 ("c<strong>a</strong>ca")，下标为 2 ("bb<strong>b</strong>b")，下标为 3 ("cac<strong>a</strong>")
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>words = ["abba","baab"], target = "bab"
<b>输出：</b>4
<b>解释：</b>总共有 4 种不同形成 target 的方法。
"bab" -> 下标为 0 ("<strong>b</strong>aab")，下标为 1 ("b<strong>a</strong>ab")，下标为 2 ("ab<strong>b</strong>a")
"bab" -> 下标为 0 ("<strong>b</strong>aab")，下标为 1 ("b<strong>a</strong>ab")，下标为 3 ("baa<strong>b</strong>")
"bab" -> 下标为 0 ("<strong>b</strong>aab")，下标为 2 ("ba<strong>a</strong>b")，下标为 3 ("baa<strong>b</strong>")
"bab" -> 下标为 1 ("a<strong>b</strong>ba")，下标为 2 ("ba<strong>a</strong>b")，下标为 3 ("baa<strong>b</strong>")
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>words = ["abcd"], target = "abcd"
<b>输出：</b>1
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<b>输入：</b>words = ["abab","baba","abba","baab"], target = "abba"
<b>输出：</b>16
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= words.length <= 1000</code></li>
	<li><code>1 <= words[i].length <= 1000</code></li>
	<li><code>words</code> 中所有单词长度相同。</li>
	<li><code>1 <= target.length <= 1000</code></li>
	<li><code>words[i]</code> 和 <code>target</code> 都仅包含小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 20 ms

```java
class Solution {
    public int numWays(String[] words, String target) {
        final int MOD = (int)1e9 + 7;
        int lw = words[0].length(), lt = target.length();
        long[] dpa = new long[lw];
        long[][] n26 = new long[lw][26];
        for (String w : words) {
            for (int i = 0; i < lw; ++i) {
                ++n26[i][w.charAt(i) - 'a'];
            }
        }
        // System.out.println(Arrays.deepToString(n26));
        int c = target.charAt(0) - 'a';
        for (int j = 0; j <= lw - lt; ++j) {
            dpa[j] = n26[j][c];
            if (j > 0) dpa[j] += dpa[j - 1];
        }
        // System.out.println(Arrays.toString(dpa));
        for (int i = 1; i < lt; ++i) {
            c = target.charAt(i) - 'a';
            for (int j = lw - (lt - i); j >= i; --j) {
                dpa[j] = dpa[j - 1] * n26[j][c];
                dpa[j] %= MOD;
            }
            for (int j = i + 1; j <= lw - (lt - i); ++j) {
                dpa[j] += dpa[j - 1];
                dpa[j] %= MOD;
            }
        // System.out.println(Arrays.toString(dpa));
        }
        return (int)dpa[lw - 1];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-ways-to-form-a-target-string-given-a-dictionary/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-ways-to-form-a-target-string-given-a-dictionary/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-ways-to-form-a-target-string-given-a-dictionary/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-ways-to-form-a-target-string-given-a-dictionary/)

[回到目录](../README.md)