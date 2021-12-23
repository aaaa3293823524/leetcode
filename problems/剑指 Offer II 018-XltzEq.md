# 剑指 Offer II 018. XltzEq | 有效的回文

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个字符串 <code>s</code> ，验证 <code>s</code>&nbsp;是否是&nbsp;<strong>回文串&nbsp;</strong>，只考虑字母和数字字符，可以忽略字母的大小写。</p>

<p>本题中，将空字符串定义为有效的&nbsp;<strong>回文串&nbsp;</strong>。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入: </strong>s =<strong> </strong>&quot;A man, a plan, a canal: Panama&quot;
<strong>输出:</strong> true
<strong>解释：</strong>&quot;amanaplanacanalpanama&quot; 是回文串</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> s = &quot;race a car&quot;
<strong>输出:</strong> false
解释：&quot;raceacar&quot; 不是回文串</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 2 * 10<sup>5</sup></code></li>
	<li>字符串 <code>s</code> 由 ASCII 字符组成</li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 125&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/valid-palindrome/">https://leetcode-cn.com/problems/valid-palindrome/</a></p>




## Solution

Language: **java**  /  Runtime: 9 ms

```java
class Solution {
    public boolean isPalindrome(String s) {
        if(s==null)return true;
        StringBuilder stringBuilder=new StringBuilder();
        for(int i=0;i<s.length();i++) {
            if(Character.isAlphabetic(s.charAt(i)))stringBuilder.append(Character.toUpperCase(s.charAt(i)));
            if(s.charAt(i)>='0'&&s.charAt(i)<='9')stringBuilder.append(s.charAt(i));
        }
        
        String string1=stringBuilder.reverse().toString();
        String string2=stringBuilder.toString();
        System.out.println(stringBuilder.toString());
        System.out.println(stringBuilder.reverse().toString());
        return stringBuilder.toString().equals(stringBuilder.reverse().toString());
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/XltzEq/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/XltzEq/description/)

Solution: [LeetCode](https://leetcode.com/articles/XltzEq/)  /  [LeetCode中国](https://leetcode-cn.com/articles/XltzEq/)

[回到目录](../README.md)