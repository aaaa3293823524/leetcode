# 344. reverse-string | 反转字符串

## Question description

<!--If you want to use the English description, use <p>Write a function that reverses a string. The input string is given as an array of characters <code>s</code>.</p>

<p>You must do this by modifying the input array <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank">in-place</a> with <code>O(1)</code> extra memory.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = ["h","e","l","l","o"]
<strong>Output:</strong> ["o","l","l","e","h"]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = ["H","a","n","n","a","h"]
<strong>Output:</strong> ["h","a","n","n","a","H"]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> is a <a href="https://en.wikipedia.org/wiki/ASCII#Printable_characters" target="_blank">printable ascii character</a>.</li>
</ul>
 instead-->
<p>编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 <code>s</code> 的形式给出。</p>

<p>不要给另外的数组分配额外的空间，你必须<strong><a href="https://baike.baidu.com/item/原地算法" target="_blank">原地</a>修改输入数组</strong>、使用 O(1) 的额外空间解决这一问题。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = ["h","e","l","l","o"]
<strong>输出：</strong>["o","l","l","e","h"]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = ["H","a","n","n","a","h"]
<strong>输出：</strong>["h","a","n","n","a","H"]</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s[i]</code> 都是 <a href="https://baike.baidu.com/item/ASCII" target="_blank">ASCII</a> 码表中的可打印字符</li>
</ul>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution{
public void reverseString(char[] s) {
        int end = s.length;
        int half = end / 2;
        end = end - 1;
        for (int i = 0; i < half && end >= 0; ++i, --end) {
            s[i] ^= s[end];
            s[end] ^= s[i];
            s[i] ^= s[end];
        }
    }

}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-string/)

[回到目录](../README.md)