# 917. reverse-only-letters | 仅仅反转字母

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, reverse the string according to the following rules:</p>

<ul>
	<li>All the characters that are not English letters remain in the same position.</li>
	<li>All the English letters (lowercase or uppercase) should be reversed.</li>
</ul>

<p>Return <code>s</code><em> after reversing it</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "ab-cd"
<strong>Output:</strong> "dc-ba"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "a-bC-dEf-ghIj"
<strong>Output:</strong> "j-Ih-gfE-dCba"
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = "Test1ng-Leet=code-Q!"
<strong>Output:</strong> "Qedo1ct-eeLg=ntse-T!"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s</code> consists of characters with ASCII values in the range <code>[33, 122]</code>.</li>
	<li><code>s</code> does not contain <code>&#39;\&quot;&#39;</code> or <code>&#39;\\&#39;</code>.</li>
</ul>
 instead-->
<p>给定一个字符串&nbsp;<code>S</code>，返回&nbsp;&ldquo;反转后的&rdquo;&nbsp;字符串，其中不是字母的字符都保留在原地，而所有字母的位置发生反转。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>&quot;ab-cd&quot;
<strong>输出：</strong>&quot;dc-ba&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>&quot;a-bC-dEf-ghIj&quot;
<strong>输出：</strong>&quot;j-Ih-gfE-dCba&quot;
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>&quot;Test1ng-Leet=code-Q!&quot;
<strong>输出：</strong>&quot;Qedo1ct-eeLg=ntse-T!&quot;
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>S.length &lt;= 100</code></li>
	<li><code>33 &lt;= S[i].ASCIIcode &lt;= 122</code>&nbsp;</li>
	<li><code>S</code> 中不包含&nbsp;<code>\</code> or <code>&quot;</code></li>
</ol>


## Note

1 字母栈

扫描两次  第一次用栈存储  第二次扫描时遇到字母弹栈



2 记录一个反序指针  字母时用这个字母代替  否则用‘-’连接


## Solution

Language: **python3**  /  Runtime: 36 ms

```python3
class Solution(object):
    def reverseOnlyLetters(self, S):
        ans = []
        j = len(ans) - 1
        for i, x in enumerate(S):
            if x.isalpha():
                while not S[j].isalpha():
                    j -= 1
                ans.append(S[j])
                j -= 1
            else:
                ans.append(x)
        
        return "".join(ans)

```

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public String reverseOnlyLetters(String S) {
        Stack<Character> letters = new Stack();
        for (char c: S.toCharArray())
            if (Character.isLetter(c))
                letters.push(c);

        StringBuilder ans = new StringBuilder();
        for (char c: S.toCharArray()) {
            if (Character.isLetter(c))
                ans.append(letters.pop());
            else
                ans.append(c);
        }

        return ans.toString();
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-only-letters/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-only-letters/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-only-letters/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-only-letters/)

[回到目录](../README.md)