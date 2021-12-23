# 1961. check-if-string-is-a-prefix-of-array | 检查字符串是否为数组前缀

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code> and an array of strings <code>words</code>, determine whether <code>s</code> is a <strong>prefix string</strong> of <code>words</code>.</p>

<p>A string <code>s</code> is a <strong>prefix string</strong> of <code>words</code> if <code>s</code> can be made by concatenating the first <code>k</code> strings in <code>words</code> for some <strong>positive</strong> <code>k</code> no larger than <code>words.length</code>.</p>

<p>Return <code>true</code><em> if </em><code>s</code><em> is a <strong>prefix string</strong> of </em><code>words</code><em>, or </em><code>false</code><em> otherwise</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;iloveleetcode&quot;, words = [&quot;i&quot;,&quot;love&quot;,&quot;leetcode&quot;,&quot;apples&quot;]
<strong>Output:</strong> true
<strong>Explanation:</strong>
s can be made by concatenating &quot;i&quot;, &quot;love&quot;, and &quot;leetcode&quot; together.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;iloveleetcode&quot;, words = [&quot;apples&quot;,&quot;i&quot;,&quot;love&quot;,&quot;leetcode&quot;]
<strong>Output:</strong> false
<strong>Explanation:</strong>
It is impossible to make s using a prefix of arr.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 100</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 20</code></li>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>words[i]</code> and <code>s</code> consist of only lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个字符串 <code>s</code> 和一个字符串数组 <code>words</code> ，请你判断 <code>s</code> 是否为 <code>words</code> 的 <strong>前缀字符串</strong> 。</p>

<p>字符串 <code>s</code> 要成为 <code>words</code> 的 <strong>前缀字符串</strong> ，需要满足：<code>s</code> 可以由 <code>words</code> 中的前 <code>k</code>（<code>k</code> 为 <strong>正数</strong> ）个字符串按顺序相连得到，且 <code>k</code> 不超过 <code>words.length</code> 。</p>

<p>如果 <code>s</code> 是 <code>words</code> 的 <strong>前缀字符串</strong> ，返回 <code>true</code> ；否则，返回 <code>false</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "iloveleetcode", words = ["i","love","leetcode","apples"]
<strong>输出：</strong>true
<strong>解释：</strong>
s 可以由 "i"、"love" 和 "leetcode" 相连得到。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "iloveleetcode", words = ["apples","i","love","leetcode"]
<strong>输出：</strong>false
<strong>解释：</strong>
数组的前缀相连无法得到 s 。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= words.length &lt;= 100</code></li>
	<li><code>1 &lt;= words[i].length &lt;= 20</code></li>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>words[i]</code> 和 <code>s</code> 仅由小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public boolean isPrefixString(String s, String[] words) {
    int strLen = s.length();
    int index = 0;
    for (String word : words) {
        int len = word.length();
        for (int i = 0; i < len; i++) {
            if (index < strLen && s.charAt(index) == word.charAt(i)) {
                index++;
            } else {
                return false;
            }
        }
        if (index == strLen) {
            return true;
        }
    }
    return false;
}
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/check-if-string-is-a-prefix-of-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/check-if-string-is-a-prefix-of-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/check-if-string-is-a-prefix-of-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/check-if-string-is-a-prefix-of-array/)

[回到目录](../README.md)