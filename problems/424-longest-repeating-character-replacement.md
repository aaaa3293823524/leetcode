﻿# 424. longest-repeating-character-replacement | 替换后的最长重复字符

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>&nbsp;that consists of only uppercase English letters, you can perform at most <code>k</code> operations on that string.</p>

<p>In one operation, you can choose <strong>any</strong> character of the string and change it to any other uppercase English character.</p>

<p>Find the length of the longest sub-string containing all repeating letters you can get after performing the above operations.</p>

<p><b>Note:</b><br />
Both the string&#39;s length and <i>k</i> will not exceed 10<sup>4</sup>.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b>
s = &quot;ABAB&quot;, k = 2

<b>Output:</b>
4

<b>Explanation:</b>
Replace the two &#39;A&#39;s with two &#39;B&#39;s or vice versa.
</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b>
s = &quot;AABABBA&quot;, k = 1

<b>Output:</b>
4

<b>Explanation:</b>
Replace the one &#39;A&#39; in the middle with &#39;B&#39; and form &quot;AABBBBA&quot;.
The substring &quot;BBBB&quot; has the longest repeating letters, which is 4.
</pre>

<p>&nbsp;</p>
 instead-->
<p>给你一个仅由大写英文字母组成的字符串，你可以将任意位置上的字符替换成另外的字符，总共可最多替换&nbsp;<em>k&nbsp;</em>次。在执行上述操作后，找到包含重复字母的最长子串的长度。</p>

<p><strong>注意:</strong><br>
字符串长度 和 <em>k </em>不会超过&nbsp;10<sup>4</sup>。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong>
s = &quot;ABAB&quot;, k = 2

<strong>输出:</strong>
4

<strong>解释:</strong>
用两个&#39;A&#39;替换为两个&#39;B&#39;,反之亦然。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong>
s = &quot;AABABBA&quot;, k = 1

<strong>输出:</strong>
4

<strong>解释:</strong>
将中间的一个&#39;A&#39;替换为&#39;B&#39;,字符串变为 &quot;AABBBBA&quot;。
子串 &quot;BBBB&quot; 有最长重复字母, 答案为 4。
</pre>


## Note

滑动窗口



滑动窗口，一个区间满足条件的原则是当前区间的长度<=区间内出现次数最多的字符 + k当前区间的长度<=区间内出现次数最多的字符+k，用滑动窗口维护即可。即当满足条件时，滑动窗口拓展，右端点++；不满足时，滑动窗口平移，左右端点++。滑动窗口的长度只会不断增大，遍历结束后滑动窗口的长度即为答案。






## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int characterReplacement(String s, int k) {
        int n = s.length(), res = 0, l = 0, r = 0, ma = 0;
        int[] b = new int[26];
        for (r = 0; r < n; r++) {
            int now = s.charAt(r) - 'A';
            b[now]++;
            ma = Math.max(ma, b[now]);
            if (ma + k < r - l + 1) {
                b[s.charAt(l) - 'A']--;
                l++;
            }
        }
        return n - l;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-repeating-character-replacement/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-repeating-character-replacement/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-repeating-character-replacement/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-repeating-character-replacement/)

[回到目录](../README.md)