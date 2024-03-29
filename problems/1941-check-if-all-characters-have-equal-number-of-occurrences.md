﻿# 1941. check-if-all-characters-have-equal-number-of-occurrences | 检查是否所有字符出现次数相同

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, return <code>true</code><em> if </em><code>s</code><em> is a <strong>good</strong> string, or </em><code>false</code><em> otherwise</em>.</p>

<p>A string <code>s</code> is <strong>good</strong> if <strong>all</strong> the characters that appear in <code>s</code> have the <strong>same</strong> number of occurrences (i.e., the same frequency).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abacbc&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> The characters that appear in s are &#39;a&#39;, &#39;b&#39;, and &#39;c&#39;. All characters occur 2 times in s.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aaabb&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> The characters that appear in s are &#39;a&#39; and &#39;b&#39;.
&#39;a&#39; occurs 3 times while &#39;b&#39; occurs 2 times, which is not the same number of times.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个字符串 <code>s</code> ，如果 <code>s</code> 是一个 <strong>好</strong> 字符串，请你返回 <code>true</code> ，否则请返回 <code>false</code> 。</p>

<p>如果 <code>s</code> 中出现过的 <strong>所有</strong> 字符的出现次数 <strong>相同</strong> ，那么我们称字符串 <code>s</code> 是 <strong>好</strong> 字符串。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>s = "abacbc"
<b>输出：</b>true
<b>解释：</b>s 中出现过的字符为 'a'，'b' 和 'c' 。s 中所有字符均出现 2 次。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>s = "aaabb"
<b>输出：</b>false
<b>解释：</b>s 中出现过的字符为 'a' 和 'b' 。
'a' 出现了 3 次，'b' 出现了 2 次，两者出现次数不同。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> 只包含小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 7 ms

```java
class Solution {
    public boolean areOccurrencesEqual(String s) {
        HashMap<Character, Integer>map=new HashMap<Character, Integer>();
        char[]c=s.toCharArray();
        for(int i=0;i<s.length();i++) {
            map.put(c[i],map.getOrDefault(c[i], 0)+1);
        }
        int g=map.get(c[0]);
        for(Integer t:map.values()) {
            if(g!=t)return  false;
        }
        return true;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/check-if-all-characters-have-equal-number-of-occurrences/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/check-if-all-characters-have-equal-number-of-occurrences/description/)

Solution: [LeetCode](https://leetcode.com/articles/check-if-all-characters-have-equal-number-of-occurrences/)  /  [LeetCode中国](https://leetcode-cn.com/articles/check-if-all-characters-have-equal-number-of-occurrences/)

[回到目录](../README.md)