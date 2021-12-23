# 58. length-of-last-word | 最后一个单词的长度

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code> consisting&nbsp;of some words separated by some number of spaces, return <em>the length of the <strong>last</strong> word in the string.</em></p>

<p>A <strong>word</strong> is a maximal substring consisting of non-space characters only.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Hello World&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The last word is &quot;World&quot; with length 5.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;   fly me   to   the moon  &quot;
<strong>Output:</strong> 4
<strong>Explanation:</strong> The last word is &quot;moon&quot; with length 4.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;luffy is still joyboy&quot;
<strong>Output:</strong> 6
<strong>Explanation:</strong> The last word is &quot;joyboy&quot; with length 6.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of only English letters and spaces <code>&#39; &#39;</code>.</li>
	<li>There will be at least one word in <code>s</code>.</li>
</ul>
 instead-->
<p>给你一个字符串 <code>s</code>，由若干单词组成，单词前后用一些空格字符隔开。返回字符串中最后一个单词的长度。</p>

<p><strong>单词</strong> 是指仅由字母组成、不包含任何空格字符的最大子字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "Hello World"
<strong>输出：</strong>5
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "   fly me   to   the moon  "
<strong>输出：</strong>4
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "luffy is still joyboy"
<strong>输出：</strong>6
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> 仅有英文字母和空格 <code>' '</code> 组成</li>
	<li><code>s</code> 中至少存在一个单词</li>
</ul>




## Solution

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution(object):
    def lengthOfLastWord(self, s):
        s = s.strip()
        if len(s) != 0:
            return len(s.split(' ')[-1])
        else:
            return 0


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/length-of-last-word/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/length-of-last-word/description/)

Solution: [LeetCode](https://leetcode.com/articles/length-of-last-word/)  /  [LeetCode中国](https://leetcode-cn.com/articles/length-of-last-word/)

[回到目录](../README.md)