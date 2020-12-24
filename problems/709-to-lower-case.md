# 709. to-lower-case | 转换成小写字母

## Question description

<!--If you want to use the English description, use <p>Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">&quot;Hello&quot;</span>
<strong>Output: </strong><span id="example-output-1">&quot;hello&quot;</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">&quot;here&quot;</span>
<strong>Output: </strong><span id="example-output-2">&quot;here&quot;</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">&quot;LOVELY&quot;</span>
<strong>Output: </strong><span id="example-output-3">&quot;lovely&quot;</span>
</pre>
</div>
</div>
</div> instead-->
<p>实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入: </strong>&quot;Hello&quot;
<strong>输出: </strong>&quot;hello&quot;</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入: </strong>&quot;here&quot;
<strong>输出: </strong>&quot;here&quot;</pre>

<p><strong>示例</strong><strong>&nbsp;3：</strong></p>

<pre>
<strong>输入: </strong>&quot;LOVELY&quot;
<strong>输出: </strong>&quot;lovely&quot;
</pre>




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