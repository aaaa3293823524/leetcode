# 1967. number-of-strings-that-appear-as-substrings-in-word | 作为子字符串出现在单词中的字符串数目

## Question description

<!--If you want to use the English description, use <p>Given an array of strings <code>patterns</code> and a string <code>word</code>, return <em>the <strong>number</strong> of strings in </em><code>patterns</code><em> that exist as a <strong>substring</strong> in </em><code>word</code>.</p>

<p>A <strong>substring</strong> is a contiguous sequence of characters within a string.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> patterns = [&quot;a&quot;,&quot;abc&quot;,&quot;bc&quot;,&quot;d&quot;], word = &quot;abc&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong>
- &quot;a&quot; appears as a substring in &quot;<u>a</u>bc&quot;.
- &quot;abc&quot; appears as a substring in &quot;<u>abc</u>&quot;.
- &quot;bc&quot; appears as a substring in &quot;a<u>bc</u>&quot;.
- &quot;d&quot; does not appear as a substring in &quot;abc&quot;.
3 of the strings in patterns appear as a substring in word.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> patterns = [&quot;a&quot;,&quot;b&quot;,&quot;c&quot;], word = &quot;aaaaabbbbb&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong>
- &quot;a&quot; appears as a substring in &quot;a<u>a</u>aaabbbbb&quot;.
- &quot;b&quot; appears as a substring in &quot;aaaaabbbb<u>b</u>&quot;.
- &quot;c&quot; does not appear as a substring in &quot;aaaaabbbbb&quot;.
2 of the strings in patterns appear as a substring in word.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> patterns = [&quot;a&quot;,&quot;a&quot;,&quot;a&quot;], word = &quot;ab&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> Each of the patterns appears as a substring in word &quot;<u>a</u>b&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= patterns.length &lt;= 100</code></li>
	<li><code>1 &lt;= patterns[i].length &lt;= 100</code></li>
	<li><code>1 &lt;= word.length &lt;= 100</code></li>
	<li><code>patterns[i]</code> and <code>word</code> consist of lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个字符串数组 <code>patterns</code> 和一个字符串 <code>word</code> ，统计 <code>patterns</code> 中有多少个字符串是 <code>word</code> 的子字符串。返回字符串数目。</p>

<p><strong>子字符串</strong> 是字符串中的一个连续字符序列。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>patterns = ["a","abc","bc","d"], word = "abc"
<strong>输出：</strong>3
<strong>解释：</strong>
- "a" 是 "<em><strong>a</strong></em>bc" 的子字符串。
- "abc" 是 "<em><strong>abc</strong></em>" 的子字符串。
- "bc" 是 "a<em><strong>bc</strong></em>" 的子字符串。
- "d" 不是 "abc" 的子字符串。
patterns 中有 3 个字符串作为子字符串出现在 word 中。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>patterns = ["a","b","c"], word = "aaaaabbbbb"
<strong>输出：</strong>2
<strong>解释：</strong>
- "a" 是 "a<em><strong>a</strong></em>aaabbbbb" 的子字符串。
- "b" 是 "aaaaabbbb<em><strong>b</strong></em>" 的子字符串。
- "c" 不是 "aaaaabbbbb" 的字符串。
patterns 中有 2 个字符串作为子字符串出现在 word 中。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>patterns = ["a","a","a"], word = "ab"
<strong>输出：</strong>3
<strong>解释：</strong>patterns 中的每个字符串都作为子字符串出现在 word "<em><strong>a</strong></em>b" 中。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= patterns.length &lt;= 100</code></li>
	<li><code>1 &lt;= patterns[i].length &lt;= 100</code></li>
	<li><code>1 &lt;= word.length &lt;= 100</code></li>
	<li><code>patterns[i]</code> 和 <code>word</code> 由小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int numOfStrings(String[] patterns, String word) {
        int count=0;
        for(int i=0;i<patterns.length;i++) {
            if(word.indexOf(patterns[i])!=-1)count++;
        }
        return count;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-strings-that-appear-as-substrings-in-word/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-strings-that-appear-as-substrings-in-word/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-strings-that-appear-as-substrings-in-word/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-strings-that-appear-as-substrings-in-word/)

[回到目录](../README.md)