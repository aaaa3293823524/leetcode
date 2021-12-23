# 583. delete-operation-for-two-strings | 两个字符串的删除操作

## Question description

<!--If you want to use the English description, use <p>Given two strings <code>word1</code> and <code>word2</code>, return <em>the minimum number of <strong>steps</strong> required to make</em> <code>word1</code> <em>and</em> <code>word2</code> <em>the same</em>.</p>

<p>In one <strong>step</strong>, you can delete exactly one character in either string.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> word1 = &quot;sea&quot;, word2 = &quot;eat&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> You need one step to make &quot;sea&quot; to &quot;ea&quot; and another step to make &quot;eat&quot; to &quot;ea&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> word1 = &quot;leetcode&quot;, word2 = &quot;etco&quot;
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= word1.length, word2.length &lt;= 500</code></li>
	<li><code>word1</code> and <code>word2</code> consist of only lowercase English letters.</li>
</ul>
 instead-->
<p>给定两个单词&nbsp;<em>word1&nbsp;</em>和&nbsp;<em>word2</em>，找到使得&nbsp;<em>word1&nbsp;</em>和&nbsp;<em>word2&nbsp;</em>相同所需的最小步数，每步可以删除任意一个字符串中的一个字符。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入:</strong> &quot;sea&quot;, &quot;eat&quot;
<strong>输出:</strong> 2
<strong>解释:</strong> 第一步将&quot;sea&quot;变为&quot;ea&quot;，第二步将&quot;eat&quot;变为&quot;ea&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>给定单词的长度不超过500。</li>
	<li>给定单词中的字符只含有小写字母。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int minDistance(String word1, String word2) {
        int m = word1.length(), n = word2.length();
        int[][] dp = new int[m + 1][n + 1];
        for (int i = 1; i <= m; i++) {
            dp[i][0] = i;
        }
        for (int j = 1; j <= n; j++) {
            dp[0][j] = j;
        }
        for (int i = 1; i <= m; i++) {
            char c1 = word1.charAt(i - 1);
            for (int j = 1; j <= n; j++) {
                char c2 = word2.charAt(j - 1);
                if (c1 == c2) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    dp[i][j] = Math.min(dp[i - 1][j], dp[i][j - 1]) + 1;
                }
            }
        }
        return dp[m][n];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/delete-operation-for-two-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/delete-operation-for-two-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/delete-operation-for-two-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/delete-operation-for-two-strings/)

[回到目录](../README.md)