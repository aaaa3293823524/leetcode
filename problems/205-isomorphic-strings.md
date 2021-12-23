# 205. isomorphic-strings | 同构字符串

## Question description

<!--If you want to use the English description, use <p>Given two strings <code>s</code> and <code>t</code>, <em>determine if they are isomorphic</em>.</p>

<p>Two strings <code>s</code> and <code>t</code> are isomorphic if the characters in <code>s</code> can be replaced to get <code>t</code>.</p>

<p>All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "egg", t = "add"
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "foo", t = "bar"
<strong>Output:</strong> false
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = "paper", t = "title"
<strong>Output:</strong> true
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>t.length == s.length</code></li>
	<li><code>s</code> and <code>t</code> consist of any valid ascii character.</li>
</ul>
 instead-->
<p>给定两个字符串 <em><strong>s </strong></em>和 <strong><em>t</em></strong>，判断它们是否是同构的。</p>

<p>如果 <em><strong>s </strong></em>中的字符可以按某种映射关系替换得到 <strong><em>t </em></strong>，那么这两个字符串是同构的。</p>

<p>每个出现的字符都应当映射到另一个字符，同时不改变字符的顺序。不同字符不能映射到同一个字符上，相同字符只能映射到同一个字符上，字符可以映射到自己本身。</p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入：</strong><strong><em>s</em></strong> = <code>"egg", </code><strong><em>t = </em></strong><code>"add"</code>
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong><strong><em>s</em></strong> = <code>"foo", </code><strong><em>t = </em></strong><code>"bar"</code>
<strong>输出：</strong>false</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong><strong><em>s</em></strong> = <code>"paper", </code><strong><em>t = </em></strong><code>"title"</code>
<strong>输出：</strong>true</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li>可以假设 <em><strong>s </strong></em>和 <strong><em>t </em></strong>长度相同。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 30 ms

```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        Map<Character,Character> map = new HashMap<>();
        if(s.length()!=t.length())return false;
        
        for(int i = 0;i<s.length();i++){
            char ss = s.charAt(i);
            char tt = t.charAt(i);
            if(map.containsKey(ss)){
                if(map.get(ss)!=tt)return false;
            }else{
                if(map.containsValue(tt))return false;
                map.put(ss,tt);
            }

 }              
        return true; 
        }
        
        
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/isomorphic-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/isomorphic-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/isomorphic-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/isomorphic-strings/)

[回到目录](../README.md)