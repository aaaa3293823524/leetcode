# 557. reverse-words-in-a-string-iii | 反转字符串中的单词 III

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "Let's take LeetCode contest"
<strong>Output:</strong> "s'teL ekat edoCteeL tsetnoc"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "God Ding"
<strong>Output:</strong> "doG gniD"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> contains printable <strong>ASCII</strong> characters.</li>
	<li><code>s</code> does not contain any leading or trailing spaces.</li>
	<li>There is <strong>at least one</strong> word in <code>s</code>.</li>
	<li>All the words in <code>s</code> are separated by a single space.</li>
</ul>
 instead-->
<p>给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>&quot;Let&#39;s take LeetCode contest&quot;
<strong>输出：</strong>&quot;s&#39;teL ekat edoCteeL tsetnoc&quot;
</pre>

<p>&nbsp;</p>

<p><strong><strong><strong><strong>提示：</strong></strong></strong></strong></p>

<ul>
	<li>在字符串中，每个单词由单个空格分隔，并且字符串中不会有任何额外的空格。</li>
</ul>




## Solution

Language: **python3**  /  Runtime: 52 ms

```python3
class Solution:
    def reverseWords(self, s: str) -> str:
        g=[]
        l=s.split()
        for i in l:
            g.append(i[::-1])
        return " ".join(g)
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-words-in-a-string-iii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-words-in-a-string-iii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-words-in-a-string-iii/)

[回到目录](../README.md)