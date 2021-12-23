# 316. remove-duplicate-letters | 去除重复字母

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, remove duplicate letters so that every letter appears once and only once. You must make sure your result is <strong>the smallest in lexicographical order</strong> among all possible results.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;bcabc&quot;
<strong>Output:</strong> &quot;abc&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;cbacdcbc&quot;
<strong>Output:</strong> &quot;acdb&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Note:</strong> This question is the same as 1081: <a href="https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/" target="_blank">https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/</a></p>
 instead-->
<p>给你一个字符串 <code>s</code> ，请你去除字符串中重复的字母，使得每个字母只出现一次。需保证 <strong>返回结果的字典序最小</strong>（要求不能打乱其他字符的相对位置）。</p>

<p><strong>注意：</strong>该题与 1081 <a href="https://leetcode-cn.com/problems/smallest-subsequence-of-distinct-characters">https://leetcode-cn.com/problems/smallest-subsequence-of-distinct-characters</a> 相同</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong><code>s = "bcabc"</code>
<strong>输出<code>：</code></strong><code>"abc"</code>
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong><code>s = "cbacdcbc"</code>
<strong>输出：</strong><code>"acdb"</code></pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 10<sup>4</sup></code></li>
	<li><code>s</code> 由小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public String removeDuplicateLetters(String s) {
        boolean[] vis = new boolean[26];
        int[] num = new int[26];
        for (int i = 0; i < s.length(); i++) {
            num[s.charAt(i) - 'a']++;
        }

        StringBuffer sb = new StringBuffer();
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (!vis[ch - 'a']) {
                while (sb.length() > 0 && sb.charAt(sb.length() - 1) > ch) {
                    if (num[sb.charAt(sb.length() - 1) - 'a'] > 0) {
                        vis[sb.charAt(sb.length() - 1) - 'a'] = false;
                        sb.deleteCharAt(sb.length() - 1);
                    } else {
                        break;
                    }
                }
                vis[ch - 'a'] = true;
                sb.append(ch);
            }
            num[ch - 'a'] -= 1;
        }
        return sb.toString();
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/remove-duplicate-letters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-duplicate-letters/description/)

Solution: [LeetCode](https://leetcode.com/articles/remove-duplicate-letters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/remove-duplicate-letters/)

[回到目录](../README.md)