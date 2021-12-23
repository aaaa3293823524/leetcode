﻿# 剑指 Offer II 095. qJnOS7 | 最长公共子序列

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定两个字符串&nbsp;<code>text1</code> 和&nbsp;<code>text2</code>，返回这两个字符串的最长 <strong>公共子序列</strong> 的长度。如果不存在 <strong>公共子序列</strong> ，返回 <code>0</code> 。</p>

<p>一个字符串的&nbsp;<strong>子序列</strong><em>&nbsp;</em>是指这样一个新的字符串：它是由原字符串在不改变字符的相对顺序的情况下删除某些字符（也可以不删除任何字符）后组成的新字符串。</p>

<ul>
	<li>例如，<code>&quot;ace&quot;</code> 是 <code>&quot;abcde&quot;</code> 的子序列，但 <code>&quot;aec&quot;</code> 不是 <code>&quot;abcde&quot;</code> 的子序列。</li>
</ul>

<p>两个字符串的 <strong>公共子序列</strong> 是这两个字符串所共同拥有的子序列。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>text1 = &quot;abcde&quot;, text2 = &quot;ace&quot; 
<strong>输出：</strong>3  
<strong>解释：</strong>最长公共子序列是 &quot;ace&quot; ，它的长度为 3 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>text1 = &quot;abc&quot;, text2 = &quot;abc&quot;
<strong>输出：</strong>3
<strong>解释：</strong>最长公共子序列是 &quot;abc&quot; ，它的长度为 3 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>text1 = &quot;abc&quot;, text2 = &quot;def&quot;
<strong>输出：</strong>0
<strong>解释：</strong>两个字符串没有公共子序列，返回 0 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= text1.length, text2.length &lt;= 1000</code></li>
	<li><code>text1</code> 和&nbsp;<code>text2</code> 仅由小写英文字符组成。</li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 1143&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/longest-common-subsequence/">https://leetcode-cn.com/problems/longest-common-subsequence/</a></p>




## Solution

Language: **java**  /  Runtime: 10 ms

```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int len1=text1.length(),len2=text2.length();
        int[][] dp=new int[len1+1][len2+1];
        //dp[0][0]=0;
        for(int i=1;i<=len1;i++) {
            char c1 = text1.charAt(i - 1);
            for(int j=1;j<=len2;j++) {
                char c2 = text2.charAt(j - 1);
                if (c1 == c2) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        return dp[len1][len2];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/qJnOS7/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/qJnOS7/description/)

Solution: [LeetCode](https://leetcode.com/articles/qJnOS7/)  /  [LeetCode中国](https://leetcode-cn.com/articles/qJnOS7/)

[回到目录](../README.md)