# 2000. reverse-prefix-of-word | 反转单词前缀

## Question description

<!--If you want to use the English description, use <p>Given a <strong>0-indexed</strong> string <code>word</code> and a character <code>ch</code>, <strong>reverse</strong> the segment of <code>word</code> that starts at index <code>0</code> and ends at the index of the <strong>first occurrence</strong> of <code>ch</code> (<strong>inclusive</strong>). If the character <code>ch</code> does not exist in <code>word</code>, do nothing.</p>

<ul>
	<li>For example, if <code>word = &quot;abcdefd&quot;</code> and <code>ch = &quot;d&quot;</code>, then you should <strong>reverse</strong> the segment that starts at <code>0</code> and ends at <code>3</code> (<strong>inclusive</strong>). The resulting string will be <code>&quot;<u>dcba</u>efd&quot;</code>.</li>
</ul>

<p>Return <em>the resulting string</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;<u>abcd</u>efd&quot;, ch = &quot;d&quot;
<strong>Output:</strong> &quot;<u>dcba</u>efd&quot;
<strong>Explanation:</strong>&nbsp;The first occurrence of &quot;d&quot; is at index 3. 
Reverse the part of word from 0 to 3 (inclusive), the resulting string is &quot;dcbaefd&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;<u>xyxz</u>xe&quot;, ch = &quot;z&quot;
<strong>Output:</strong> &quot;<u>zxyx</u>xe&quot;
<strong>Explanation:</strong>&nbsp;The first and only occurrence of &quot;z&quot; is at index 3.
Reverse the part of word from 0 to 3 (inclusive), the resulting string is &quot;zxyxxe&quot;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> word = &quot;abcd&quot;, ch = &quot;z&quot;
<strong>Output:</strong> &quot;abcd&quot;
<strong>Explanation:</strong>&nbsp;&quot;z&quot; does not exist in word.
You should not do any reverse operation, the resulting string is &quot;abcd&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= word.length &lt;= 250</code></li>
	<li><code>word</code> consists of lowercase English letters.</li>
	<li><code>ch</code> is a lowercase English letter.</li>
</ul>
 instead-->
<p>给你一个下标从 <strong>0</strong> 开始的字符串 <code>word</code> 和一个字符 <code>ch</code> 。找出 <code>ch</code> 第一次出现的下标 <code>i</code> ，<strong>反转 </strong><code>word</code> 中从下标 <code>0</code> 开始、直到下标 <code>i</code> 结束（含下标 <code>i</code> ）的那段字符。如果 <code>word</code> 中不存在字符 <code>ch</code> ，则无需进行任何操作。</p>

<ul>
	<li>例如，如果 <code>word = "abcdefd"</code> 且 <code>ch = "d"</code> ，那么你应该 <strong>反转</strong> 从下标 0 开始、直到下标 <code>3</code> 结束（含下标 <code>3</code> ）。结果字符串将会是 <code>"<em><strong>dcba</strong></em>efd"</code> 。</li>
</ul>

<p>返回 <strong>结果字符串</strong> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>word = "<em><strong>abcd</strong></em>efd", ch = "d"
<strong>输出：</strong>"<em><strong>dcba</strong></em>efd"
<strong>解释：</strong>"d" 第一次出现在下标 3 。 
反转从下标 0 到下标 3（含下标 3）的这段字符，结果字符串是 "dcbaefd" 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>word = "<em><strong>xyxz</strong></em>xe", ch = "z"
<strong>输出：</strong>"<em><strong>zxyx</strong></em>xe"
<strong>解释：</strong>"z" 第一次也是唯一一次出现是在下标 3 。
反转从下标 0 到下标 3（含下标 3）的这段字符，结果字符串是 "zxyxxe" 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>word = "abcd", ch = "z"
<strong>输出：</strong>"abcd"
<strong>解释：</strong>"z" 不存在于 word 中。
无需执行反转操作，结果字符串是 "abcd" 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= word.length &lt;= 250</code></li>
	<li><code>word</code> 由小写英文字母组成</li>
	<li><code>ch</code> 是一个小写英文字母</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public String reversePrefix(String word, char ch) {
        int t=-1;
        char[]c=word.toCharArray();
        for(int i=0;i<c.length;i++) {
            if(c[i]==ch) {
                t=i;
                break;
            }
        }
        if(t==-1)return word;
        return new StringBuilder(word.substring(0,t+1)).reverse().toString()+word.substring(t+1);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-prefix-of-word/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-prefix-of-word/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-prefix-of-word/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-prefix-of-word/)

[回到目录](../README.md)