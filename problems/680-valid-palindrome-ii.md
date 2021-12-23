# 680. valid-palindrome-ii | 验证回文字符串 Ⅱ

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, return <code>true</code> <em>if the </em><code>s</code><em> can be palindrome after deleting <strong>at most one</strong> character from it</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aba&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abca&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> You could delete the character &#39;c&#39;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abc&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
 instead-->
<p>给定一个非空字符串 <code>s</code>，<strong>最多</strong>删除一个字符。判断是否能成为回文字符串。</p>

<p> </p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> s = "aba"
<strong>输出:</strong> true
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> s = "abca"
<strong>输出:</strong> true
<strong>解释:</strong> 你可以删除c字符。
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> s = "abc"
<strong>输出:</strong> false</pre>

<p> </p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 <= s.length <= 10<sup>5</sup></code></li>
	<li><code>s</code> 由小写英文字母组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public boolean validPalindrome(String s) {
        int low = 0, high = s.length() - 1;
        while (low < high) {
            char c1 = s.charAt(low), c2 = s.charAt(high);
            if (c1 == c2) {
                ++low;
                --high;
            } else {
                return validPalindrome(s, low, high - 1) || validPalindrome(s, low + 1, high);
            }
        }
        return true;
    }

    public boolean validPalindrome(String s, int low, int high) {
        for (int i = low, j = high; i < j; ++i, --j) {
            char c1 = s.charAt(i), c2 = s.charAt(j);
            if (c1 != c2) {
                return false;
            }
        }
        return true;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/valid-palindrome-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-palindrome-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/valid-palindrome-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/valid-palindrome-ii/)

[回到目录](../README.md)