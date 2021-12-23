﻿# 1531. string-compression-ii | 压缩字符串 II

## Question description

<!--If you want to use the English description, use <p><a href="http://en.wikipedia.org/wiki/Run-length_encoding">Run-length encoding</a> is a string compression method that works by&nbsp;replacing consecutive identical characters (repeated 2 or more times) with the concatenation of the character and the number marking the count of the characters (length of the run). For example, to compress the string&nbsp;<code>&quot;aabccc&quot;</code>&nbsp;we replace <font face="monospace"><code>&quot;aa&quot;</code></font>&nbsp;by&nbsp;<font face="monospace"><code>&quot;a2&quot;</code></font>&nbsp;and replace <font face="monospace"><code>&quot;ccc&quot;</code></font>&nbsp;by&nbsp;<font face="monospace"><code>&quot;c3&quot;</code></font>. Thus the compressed string becomes <font face="monospace"><code>&quot;a2bc3&quot;</code>.</font></p>

<p>Notice that in this problem, we are not adding&nbsp;<code>&#39;1&#39;</code>&nbsp;after single characters.</p>

<p>Given a&nbsp;string <code>s</code>&nbsp;and an integer <code>k</code>. You need to delete <strong>at most</strong>&nbsp;<code>k</code> characters from&nbsp;<code>s</code>&nbsp;such that the run-length encoded version of <code>s</code>&nbsp;has minimum length.</p>

<p>Find the <em>minimum length of the run-length encoded&nbsp;version of </em><code>s</code><em> after deleting at most </em><code>k</code><em> characters</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aaabcccd&quot;, k = 2
<strong>Output:</strong> 4
<b>Explanation: </b>Compressing s without deleting anything will give us &quot;a3bc3d&quot; of length 6. Deleting any of the characters &#39;a&#39; or &#39;c&#39; would at most decrease the length of the compressed string to 5, for instance delete 2 &#39;a&#39; then we will have s = &quot;abcccd&quot; which compressed is abc3d. Therefore, the optimal way is to delete &#39;b&#39; and &#39;d&#39;, then the compressed version of s will be &quot;a3c3&quot; of length 4.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aabbaa&quot;, k = 2
<strong>Output:</strong> 2
<b>Explanation: </b>If we delete both &#39;b&#39; characters, the resulting compressed string would be &quot;a4&quot; of length 2.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aaaaaaaaaaa&quot;, k = 0
<strong>Output:</strong> 3
<strong>Explanation: </strong>Since k is zero, we cannot delete anything. The compressed string is &quot;a11&quot; of length 3.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>0 &lt;= k &lt;= s.length</code></li>
	<li><code>s</code> contains only lowercase English letters.</li>
</ul>
 instead-->
<p><a href="https://baike.baidu.com/item/%E8%A1%8C%E7%A8%8B%E9%95%BF%E5%BA%A6%E7%BC%96%E7%A0%81/2931940?fr=aladdin" target="_blank">行程长度编码</a> 是一种常用的字符串压缩方法，它将连续的相同字符（重复 2 次或更多次）替换为字符和表示字符计数的数字（行程长度）。例如，用此方法压缩字符串 <code>&quot;aabccc&quot;</code> ，将 <code>&quot;aa&quot;</code> 替换为 <code>&quot;a2&quot;</code> ，<code>&quot;ccc&quot;</code> 替换为` <code>&quot;c3&quot;</code> 。因此压缩后的字符串变为 <code>&quot;a2bc3&quot;</code> 。</p>

<p>注意，本问题中，压缩时没有在单个字符后附加计数 <code>&#39;1&#39;</code> 。</p>

<p>给你一个字符串 <code>s</code> 和一个整数 <code>k</code> 。你需要从字符串 <code>s</code> 中删除最多 <code>k</code> 个字符，以使 <code>s</code> 的行程长度编码长度最小。</p>

<p>请你返回删除最多 <code>k</code> 个字符后，<code>s</code> <strong>行程长度编码的最小长度</strong> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = &quot;aaabcccd&quot;, k = 2
<strong>输出：</strong>4
<strong>解释：</strong>在不删除任何内容的情况下，压缩后的字符串是 &quot;a3bc3d&quot; ，长度为 6 。最优的方案是删除 &#39;b&#39; 和 &#39;d&#39;，这样一来，压缩后的字符串为 &quot;a3c3&quot; ，长度是 4 。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = &quot;aabbaa&quot;, k = 2
<strong>输出：</strong>2
<strong>解释：</strong>如果删去两个 &#39;b&#39; 字符，那么压缩后的字符串是长度为 2 的 &quot;a4&quot; 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = &quot;aaaaaaaaaaa&quot;, k = 0
<strong>输出：</strong>3
<strong>解释：</strong>由于 k 等于 0 ，不能删去任何字符。压缩后的字符串是 &quot;a11&quot; ，长度为 3 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>0 &lt;= k &lt;= s.length</code></li>
	<li><code>s</code> 仅包含小写英文字母</li>
</ul>




## Solution

Language: **java**  /  Runtime: 25 ms

```java
class Solution {
    public int getLengthOfOptimalCompression(String s, int k) {
        int n = s.length();
        int[][] f = new int[n + 1][k + 1];
        for (int i = 0; i <= n; i++) {
            Arrays.fill(f[i], Integer.MAX_VALUE >> 1);
        }
        f[0][0] = 0;
        for (int i = 1; i <= n; ++i) {
            for (int j = 0; j <= k && j <= i; ++j) {
                if (j > 0) {
                    f[i][j] = f[i - 1][j - 1];
                }
                int same = 0, diff = 0;
                for (int i0 = i; i0 >= 1 && diff <= j; --i0) {
                    if (s.charAt(i0 - 1) == s.charAt(i - 1)) {
                        ++same;
                        f[i][j] = Math.min(f[i][j], f[i0 - 1][j - diff] + calc(same));
                    } else {
                        ++diff;
                    }
                }
            }
        }
        
        return f[n][k];
    }

    public int calc(int x) {
        if (x == 1) {
            return 1;
        }
        if (x < 10) {
            return 2;
        }
        if (x < 100) {
            return 3;
        }
        return 4;
    }
}

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/string-compression-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/string-compression-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/string-compression-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/string-compression-ii/)

[回到目录](../README.md)