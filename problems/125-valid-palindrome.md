# 125. valid-palindrome | 验证回文串

## Question description

<!--If you want to use the English description, use <p>Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.</p>

<p><strong>Note:</strong>&nbsp;For the purpose of this problem, we define empty string as valid palindrome.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> &quot;A man, a plan, a canal: Panama&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> &quot;race a car&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>s</code> consists only of printable ASCII characters.</li>
</ul>
 instead-->
<p>给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。</p>

<p><strong>说明：</strong>本题中，我们将空字符串定义为有效的回文串。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> &quot;A man, a plan, a canal: Panama&quot;
<strong>输出:</strong> true
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> &quot;race a car&quot;
<strong>输出:</strong> false
</pre>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
 public boolean isPalindrome(String s) {
        char[] cs = s.toCharArray();
        int cnt = 0, j = 0;
        for (int i = 0; i < cs.length; i++) {
            if (('0' <= cs[i] && cs[i] <= '9') || ('a' <= cs[i] && cs[i] <= 'z')) {
                cs[cnt++] = cs[i];
            } else if ('A' <= cs[i] && cs[i] <= 'Z') {
                cs[cnt++] = (char) (cs[i] - 'A' + 'a');
            }
        }
        cnt--;
        while (j < cnt) if (cs[j++] != cs[cnt--]) return false;
        return true;
    }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/valid-palindrome/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-palindrome/description/)

Solution: [LeetCode](https://leetcode.com/articles/valid-palindrome/)  /  [LeetCode中国](https://leetcode-cn.com/articles/valid-palindrome/)

[回到目录](../README.md)