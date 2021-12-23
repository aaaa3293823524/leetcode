# 709. to-lower-case | 转换成小写字母

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, return <em>the string after replacing every uppercase letter with the same lowercase letter</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;Hello&quot;
<strong>Output:</strong> &quot;hello&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;here&quot;
<strong>Output:</strong> &quot;here&quot;
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;LOVELY&quot;
<strong>Output:</strong> &quot;lovely&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s</code> consists of printable ASCII characters.</li>
</ul>
 instead-->
<p>给你一个字符串 <code>s</code> ，将该字符串中的大写字母转换成相同的小写字母，返回新的字符串。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "Hello"
<strong>输出：</strong>"hello"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "here"
<strong>输出：</strong>"here"
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "LOVELY"
<strong>输出：</strong>"lovely"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 100</code></li>
	<li><code>s</code> 由 ASCII 字符集中的可打印字符组成</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public String toLowerCase(String str) {
        String ans="";
        for(int i=0;i<str.length();i++)
        {   
            char a=str.charAt(i);
            a=tolowercase(a);
            ans+=a;
        }
        return ans;
    }
    private char tolowercase(char t)
    {
        if(t>='A' && t<='Z')
        {
            t=(char)(t+32);
        }
        return t;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/to-lower-case/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/to-lower-case/description/)

Solution: [LeetCode](https://leetcode.com/articles/to-lower-case/)  /  [LeetCode中国](https://leetcode-cn.com/articles/to-lower-case/)

[回到目录](../README.md)