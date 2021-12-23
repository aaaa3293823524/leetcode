# 14. longest-common-prefix | 最长公共前缀

## Question description

<!--If you want to use the English description, use <p>Write a function to find the longest common prefix string amongst an array of strings.</p>

<p>If there is no common prefix, return an empty string <code>&quot;&quot;</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> strs = [&quot;flower&quot;,&quot;flow&quot;,&quot;flight&quot;]
<strong>Output:</strong> &quot;fl&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> strs = [&quot;dog&quot;,&quot;racecar&quot;,&quot;car&quot;]
<strong>Output:</strong> &quot;&quot;
<strong>Explanation:</strong> There is no common prefix among the input strings.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= strs.length &lt;= 200</code></li>
	<li><code>0 &lt;= strs[i].length &lt;= 200</code></li>
	<li><code>strs[i]</code> consists of only lower-case English letters.</li>
</ul>
 instead-->
<p>编写一个函数来查找字符串数组中的最长公共前缀。</p>

<p>如果不存在公共前缀，返回空字符串&nbsp;<code>""</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>strs = ["flower","flow","flight"]
<strong>输出：</strong>"fl"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>strs = ["dog","racecar","car"]
<strong>输出：</strong>""
<strong>解释：</strong>输入不存在公共前缀。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= strs.length &lt;= 200</code></li>
	<li><code>0 &lt;= strs[i].length &lt;= 200</code></li>
	<li><code>strs[i]</code> 仅由小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
       if (strs.length == 0) return "";
       String prefix = strs[0];
       for (int i = 1; i < strs.length; i++)
           while (strs[i].indexOf(prefix) != 0) {
               prefix = prefix.substring(0, prefix.length() - 1);
               if (prefix.isEmpty()) return "";
           }        
       return prefix;
    }
}



```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-common-prefix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-common-prefix/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-common-prefix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-common-prefix/)

[回到目录](../README.md)