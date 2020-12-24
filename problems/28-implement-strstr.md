# 28. implement-strstr | 实现 strStr()

## Question description

<!--If you want to use the English description, use <p>Implement <a href="http://www.cplusplus.com/reference/cstring/strstr/" target="_blank">strStr()</a>.</p>

<p>Return the index of the first occurrence of needle in haystack, or <code>-1</code> if <code>needle</code> is not part of <code>haystack</code>.</p>

<p><strong>Clarification:</strong></p>

<p>What should we return when <code>needle</code> is an empty string? This is a great question to ask during an interview.</p>

<p>For the purpose of this problem, we will return 0 when <code>needle</code> is an empty string. This is consistent to C&#39;s&nbsp;<a href="http://www.cplusplus.com/reference/cstring/strstr/" target="_blank">strstr()</a> and Java&#39;s&nbsp;<a href="https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf(java.lang.String)" target="_blank">indexOf()</a>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> haystack = "hello", needle = "ll"
<strong>Output:</strong> 2
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> haystack = "aaaaa", needle = "bba"
<strong>Output:</strong> -1
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> haystack = "", needle = ""
<strong>Output:</strong> 0
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= haystack.length, needle.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>haystack</code> and&nbsp;<code>needle</code> consist of only lower-case English characters.</li>
</ul>
 instead-->
<p>实现&nbsp;<a href="https://baike.baidu.com/item/strstr/811469" target="_blank">strStr()</a>&nbsp;函数。</p>

<p>给定一个&nbsp;haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回&nbsp; <strong>-1</strong>。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> haystack = &quot;hello&quot;, needle = &quot;ll&quot;
<strong>输出:</strong> 2
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入:</strong> haystack = &quot;aaaaa&quot;, needle = &quot;bba&quot;
<strong>输出:</strong> -1
</pre>

<p><strong>说明:</strong></p>

<p>当&nbsp;<code>needle</code>&nbsp;是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。</p>

<p>对于本题而言，当&nbsp;<code>needle</code>&nbsp;是空字符串时我们应当返回 0 。这与C语言的&nbsp;<a href="https://baike.baidu.com/item/strstr/811469" target="_blank">strstr()</a>&nbsp;以及 Java的&nbsp;<a href="https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf(java.lang.String)" target="_blank">indexOf()</a>&nbsp;定义相符。</p>




## Solution

Language: **java**  /  Runtime: 41 ms

```java
class Solution {
    public static int strStr(String haystack, String needle) {
        int len1=haystack.length();
        int len2=needle.length();
        if(len1<len2)return -1;
        for(int i=0;i<len1-len2+1;i++) {
            int index=i;
            int j;
            for(j=0;j<len2;) {
                if (haystack.charAt(index)==needle.charAt(j)&&index<len1&&j<len2) {
                    index++;
                    j++;
                }
                else {
                    break;
                }    
                
            }
            System.out.println(j);
            if(j==len2)return i;
        }
        return -1;
    }
}
```

Language: **python3**  /  Runtime: 44 ms

```python3
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        c=-1
        for i in range(len(haystack)-len(needle)+1):
            if haystack[i:i+len(needle)]==needle:
                c=i
                break
        return c


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/implement-strstr/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/implement-strstr/description/)

Solution: [LeetCode](https://leetcode.com/articles/implement-strstr/)  /  [LeetCode中国](https://leetcode-cn.com/articles/implement-strstr/)

[回到目录](../README.md)