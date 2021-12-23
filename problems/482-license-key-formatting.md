# 482. license-key-formatting | 密钥格式化

## Question description

<!--If you want to use the English description, use <p>You are given a license key represented as a string <code>s</code> that consists of only alphanumeric characters and dashes. The string is separated into <code>n + 1</code> groups by <code>n</code> dashes. You are also given an integer <code>k</code>.</p>

<p>We want to reformat the string <code>s</code> such that each group contains exactly <code>k</code> characters, except for the first group, which could be shorter than <code>k</code> but still must contain at least one character. Furthermore, there must be a dash inserted between two groups, and you should convert all lowercase letters to uppercase.</p>

<p>Return <em>the reformatted license key</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;5F3Z-2e-9-w&quot;, k = 4
<strong>Output:</strong> &quot;5F3Z-2E9W&quot;
<strong>Explanation:</strong> The string s has been split into two parts, each part has 4 characters.
Note that the two extra dashes are not needed and can be removed.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;2-5g-3-J&quot;, k = 2
<strong>Output:</strong> &quot;2-5G-3J&quot;
<strong>Explanation:</strong> The string s has been split into three parts, each part has 2 characters except the first part as it could be shorter as mentioned above.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of English letters, digits, and dashes <code>&#39;-&#39;</code>.</li>
	<li><code>1 &lt;= k &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>有一个密钥字符串 S ，只包含字母，数字以及 &#39;-&#39;（破折号）。其中， N 个 &#39;-&#39; 将字符串分成了 N+1 组。</p>

<p>给你一个数字 K，请你重新格式化字符串，使每个分组恰好包含 K 个字符。特别地，第一个分组包含的字符个数必须小于等于 K，但至少要包含 1 个字符。两个分组之间需要用 &#39;-&#39;（破折号）隔开，并且将所有的小写字母转换为大写字母。</p>

<p>给定非空字符串 S 和数字 K，按照上面描述的规则进行格式化。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>S = &quot;5F3Z-2e-9-w&quot;, K = 4
<strong>输出：</strong>&quot;5F3Z-2E9W&quot;
<strong>解释：</strong>字符串 S 被分成了两个部分，每部分 4 个字符；
&nbsp;    注意，两个额外的破折号需要删掉。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>S = &quot;2-5g-3-J&quot;, K = 2
<strong>输出：</strong>&quot;2-5G-3J&quot;
<strong>解释：</strong>字符串 S 被分成了 3 个部分，按照前面的规则描述，第一部分的字符可以少于给定的数量，其余部分皆为 2 个字符。
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ol>
	<li>S 的长度可能很长，请按需分配大小。K 为正整数。</li>
	<li>S 只包含字母数字（a-z，A-Z，0-9）以及破折号&#39;-&#39;</li>
	<li>S 非空</li>
</ol>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 15 ms

```java
class Solution {
    public String licenseKeyFormatting(String s, int k) {
        String replace = s.replace("-", "").toUpperCase();
        int strLen = replace.length();
        int mod = replace.length() % k;
        int len = replace.length() / k;
        int index = 0;
        String[] res;
        if (mod == 0) {
            res = new String[len];
            for (int i = 0; i < strLen; i += k) {
                res[index++] = replace.substring(i, i + k);
            }
        } else {
            res = new String[len + 1];
            res[index++] = replace.substring(0, mod);
            for (int i = mod; i < strLen; i += k) {
                res[index++] = replace.substring(i, i + k);
            }
        }
        return String.join("-", res);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/license-key-formatting/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/license-key-formatting/description/)

Solution: [LeetCode](https://leetcode.com/articles/license-key-formatting/)  /  [LeetCode中国](https://leetcode-cn.com/articles/license-key-formatting/)

[回到目录](../README.md)