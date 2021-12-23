# 151. reverse-words-in-a-string | 翻转字符串里的单词

## Question description

<!--If you want to use the English description, use <p>Given an input string <code>s</code>, reverse the order of the <strong>words</strong>.</p>

<p>A <strong>word</strong> is defined as a sequence of non-space characters. The <strong>words</strong> in <code>s</code> will be separated by at least one space.</p>

<p>Return <em>a string of the words in reverse order concatenated by a single space.</em></p>

<p><b>Note</b> that <code>s</code> may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;the sky is blue&quot;
<strong>Output:</strong> &quot;blue is sky the&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;  hello world  &quot;
<strong>Output:</strong> &quot;world hello&quot;
<strong>Explanation:</strong> Your reversed string should not contain leading or trailing spaces.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;a good   example&quot;
<strong>Output:</strong> &quot;example good a&quot;
<strong>Explanation:</strong> You need to reduce multiple spaces between two words to a single space in the reversed string.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> contains English letters (upper-case and lower-case), digits, and spaces <code>&#39; &#39;</code>.</li>
	<li>There is <strong>at least one</strong> word in <code>s</code>.</li>
</ul>

<p>&nbsp;</p>
<p><b data-stringify-type="bold">Follow-up:&nbsp;</b>If the string data type is mutable in your language, can&nbsp;you solve it&nbsp;<b data-stringify-type="bold">in-place</b>&nbsp;with&nbsp;<code data-stringify-type="code">O(1)</code>&nbsp;extra space?</p>
 instead-->
<p>给你一个字符串 <code>s</code> ，逐个翻转字符串中的所有 <strong>单词</strong> 。</p>

<p><strong>单词</strong> 是由非空格字符组成的字符串。<code>s</code> 中使用至少一个空格将字符串中的 <strong>单词</strong> 分隔开。</p>

<p>请你返回一个翻转 <code>s</code> 中单词顺序并用单个空格相连的字符串。</p>

<p><strong>说明：</strong></p>

<ul>
	<li>输入字符串 <code>s</code> 可以在前面、后面或者单词间包含多余的空格。</li>
	<li>翻转后单词间应当仅用一个空格分隔。</li>
	<li>翻转后的字符串中不应包含额外的空格。</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "<code>the sky is blue</code>"
<strong>输出：</strong>"<code>blue is sky the</code>"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "  hello world  "
<strong>输出：</strong>"world hello"
<strong>解释：</strong>输入字符串可以在前面或者后面包含多余的空格，但是翻转后的字符不能包括。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "a good   example"
<strong>输出：</strong>"example good a"
<strong>解释：</strong>如果两个单词间有多余的空格，将翻转后单词间的空格减少到只含一个。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>s = "  Bob    Loves  Alice   "
<strong>输出：</strong>"Alice Loves Bob"
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>s = "Alice does not even like bob"
<strong>输出：</strong>"bob like even not does Alice"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 10<sup>4</sup></code></li>
	<li><code>s</code> 包含英文大小写字母、数字和空格 <code>' '</code></li>
	<li><code>s</code> 中 <strong>至少存在一个</strong> 单词</li>
</ul>

<ul>
</ul>

<p> </p>

<p><strong>进阶：</strong></p>

<ul>
	<li>请尝试使用 <code><em>O</em>(1)</code> 额外空间复杂度的原地解法。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 10 ms

```java
class Solution {
    public String reverseWords(String s) {
        // 除去开头和末尾的空白字符
        s = s.trim();
        // 正则匹配连续的空白字符作为分隔符分割
        List<String> wordList = Arrays.asList(s.split("\\s+"));
        Collections.reverse(wordList);
        return String.join(" ", wordList);
    }
}


```

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def reverseWords(self, s: str) -> str:
        l=s.split()[::-1]
        s=""
        for i in l:
            s+=i
            s+=" "
        
        return s.strip()
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-words-in-a-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-words-in-a-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-words-in-a-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-words-in-a-string/)

[回到目录](../README.md)