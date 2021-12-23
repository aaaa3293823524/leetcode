# 1092. shortest-common-supersequence | 最短公共超序列

## Question description

<!--If you want to use the English description, use <p>Given two strings <code>str1</code> and <code>str2</code>, return <em>the shortest string that has both </em><code>str1</code><em> and </em><code>str2</code><em> as <strong>subsequences</strong></em>. If there are multiple valid strings, return <strong>any</strong> of them.</p>

<p>A string <code>s</code> is a <strong>subsequence</strong> of string <code>t</code> if deleting some number of characters from <code>t</code> (possibly <code>0</code>) results in the string <code>s</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> str1 = &quot;abac&quot;, str2 = &quot;cab&quot;
<strong>Output:</strong> &quot;cabac&quot;
<strong>Explanation:</strong> 
str1 = &quot;abac&quot; is a subsequence of &quot;cabac&quot; because we can delete the first &quot;c&quot;.
str2 = &quot;cab&quot; is a subsequence of &quot;cabac&quot; because we can delete the last &quot;ac&quot;.
The answer provided is the shortest such string that satisfies these properties.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> str1 = &quot;aaaaaaaa&quot;, str2 = &quot;aaaaaaaa&quot;
<strong>Output:</strong> &quot;aaaaaaaa&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= str1.length, str2.length &lt;= 1000</code></li>
	<li><code>str1</code> and <code>str2</code> consist of lowercase English letters.</li>
</ul>
 instead-->
<p>给出两个字符串&nbsp;<code>str1</code> 和&nbsp;<code>str2</code>，返回同时以&nbsp;<code>str1</code>&nbsp;和&nbsp;<code>str2</code>&nbsp;作为子序列的最短字符串。如果答案不止一个，则可以返回满足条件的任意一个答案。</p>

<p>（如果从字符串 T 中删除一些字符（也可能不删除，并且选出的这些字符可以位于 T 中的&nbsp;<strong>任意位置</strong>），可以得到字符串 S，那么&nbsp;S 就是&nbsp;T 的子序列）</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>str1 = &quot;abac&quot;, str2 = &quot;cab&quot;
<strong>输出：</strong>&quot;cabac&quot;
<strong>解释：</strong>
str1 = &quot;abac&quot; 是 &quot;cabac&quot; 的一个子串，因为我们可以删去 &quot;cabac&quot; 的第一个 &quot;c&quot;得到 &quot;abac&quot;。 
str2 = &quot;cab&quot; 是 &quot;cabac&quot; 的一个子串，因为我们可以删去 &quot;cabac&quot; 末尾的 &quot;ac&quot; 得到 &quot;cab&quot;。
最终我们给出的答案是满足上述属性的最短字符串。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= str1.length, str2.length &lt;= 1000</code></li>
	<li><code>str1</code> 和&nbsp;<code>str2</code>&nbsp;都由小写英文字母组成。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 19 ms

```java
class Solution {
    public String shortestCommonSupersequence(String str1, String str2) {
        int l1 = str1.length();
        int l2 = str2.length();
        int[][] dp = new int[l1 + 1][l2 + 1];
        int[][] pred = new int[l1 + 1][l2 + 1];
        char[][] c = new char[l1 + 1][l2 + 1];

        for (int i = 1; i <= l1; i++) {
            for (int j = 1; j <= l2; j++) {
                if (dp[i - 1][j] > dp[i][j - 1]) {
                    dp[i][j] = dp[i - 1][j];
                    pred[i][j] = pred[i - 1][j];
                    c[i][j] = c[i - 1][j];
                }
                else {
                    dp[i][j] = dp[i][j - 1];
                    pred[i][j] = pred[i][j - 1];
                    c[i][j] = c[i][j - 1];
                }
                if (str1.charAt(i - 1) == str2.charAt(j - 1) && dp[i - 1][j - 1] + 1 > dp[i][j]) {
                    dp[i][j] = dp[i - 1][j - 1] + 1;
                    pred[i][j] = (i - 1) * 10000 + j - 1;
                    c[i][j] = str1.charAt(i - 1);
                }
            }
        }

        StringBuilder sb = new StringBuilder();
        int posX = l1;
        int posY = l2;
        do {
            sb.insert(0, c[posX][posY]);
            int pos = pred[posX][posY];
            posX = pos / 10000;
            posY = pos % 10000;
        } while(Character.isLowerCase(c[posX][posY]));

        String lcs = sb.toString();
        System.out.println(lcs);
        sb = new StringBuilder();
        int pos1 = 0;
        int pos2 = 0;
        int pos = 0;
        while (pos < lcs.length()) {
            char cur = lcs.charAt(pos);
            int p = pos1;
            while (pos1 < l1 && str1.charAt(pos1) != cur) {
                pos1++;
            }
            if (pos1 != p) {
                sb.append(str1, p, pos1);
            }
            p = pos2;
            while (pos2 < l2 && str2.charAt(pos2) != cur) {
                pos2++;
            }
            if (pos2 != p) {
                sb.append(str2, p, pos2);
            }
            sb.append(cur);
            pos1++;
            pos2++;
            pos++;
        }
        if (pos1 < str1.length())
            sb.append(str1.substring(pos1));
        if (pos2 < str2.length())
            sb.append(str2.substring(pos2));
        return sb.toString();
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shortest-common-supersequence/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shortest-common-supersequence/description/)

Solution: [LeetCode](https://leetcode.com/articles/shortest-common-supersequence/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shortest-common-supersequence/)

[回到目录](../README.md)