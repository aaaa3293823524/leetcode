# 434. number-of-segments-in-a-string | 字符串中的单词数

## Question description

<!--If you want to use the English description, use <p>You are given a string <code>s</code>, return <em>the number of segments in the string</em>.&nbsp;</p>

<p>A <strong>segment</strong> is defined to be a contiguous sequence of <strong>non-space characters</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Hello, my name is John&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The five segments are [&quot;Hello,&quot;, &quot;my&quot;, &quot;name&quot;, &quot;is&quot;, &quot;John&quot;]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Hello&quot;
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;love live! mu&#39;sic forever&quot;
<strong>Output:</strong> 4
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;&quot;
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 300</code></li>
	<li><code>s</code> consists of lower-case and upper-case English letters, digits or one of the following characters <code>&quot;!@#$%^&amp;*()_+-=&#39;,.:&quot;</code>.</li>
	<li>The only space character in <code>s</code> is <code>&#39; &#39;</code>.</li>
</ul>
 instead-->
<p>统计字符串中的单词个数，这里的单词指的是连续的不是空格的字符。</p>

<p>请注意，你可以假定字符串里不包括任何不可打印的字符。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> &quot;Hello, my name is John&quot;
<strong>输出:</strong> 5
<strong>解释: </strong>这里的单词是指连续的不是空格的字符，所以 &quot;Hello,&quot; 算作 1 个单词。
</pre>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int countSegments(String s) {
        int segmentCount = 0;

        for (int i = 0; i < s.length(); i++) {
            if ((i == 0 || s.charAt(i - 1) == ' ') && s.charAt(i) != ' ') {
                segmentCount++;
            }
        }

        return segmentCount;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-segments-in-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-segments-in-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-segments-in-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-segments-in-a-string/)

[回到目录](../README.md)