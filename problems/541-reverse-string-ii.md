# 541. reverse-string-ii | 反转字符串 II

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code> and an integer <code>k</code>, reverse the first <code>k</code> characters for every <code>2k</code> characters counting from the start of the string.</p>

<p>If there are fewer than <code>k</code> characters left, reverse all of them. If there are less than <code>2k</code> but greater than or equal to <code>k</code> characters, then reverse the first <code>k</code> characters and left the other as original.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "abcdefg", k = 2
<strong>Output:</strong> "bacdfeg"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = "abcd", k = 2
<strong>Output:</strong> "bacd"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of only lowercase English letters.</li>
	<li><code>1 &lt;= k &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给定一个字符串 <code>s</code> 和一个整数 <code>k</code>，从字符串开头算起，每计数至 <code>2k</code> 个字符，就反转这 <code>2k</code> 字符中的前 <code>k</code> 个字符。</p>

<ul>
	<li>如果剩余字符少于 <code>k</code> 个，则将剩余字符全部反转。</li>
	<li>如果剩余字符小于 <code>2k</code> 但大于或等于 <code>k</code> 个，则反转前 <code>k</code> 个字符，其余字符保持原样。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "abcdefg", k = 2
<strong>输出：</strong>"bacdfeg"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "abcd", k = 2
<strong>输出：</strong>"bacd"
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> 仅由小写英文组成</li>
	<li><code>1 &lt;= k &lt;= 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public String reverseStr(String s, int k) {
        if(k==0)return s;
        StringBuilder res=new StringBuilder();
        int count=0,j=0;;
        for(int i=0;i<s.length();i++) {
            count=(++count)%(2*k);
            if(count==0) {
                res.append(new StringBuilder(s.substring(j,j+k)).reverse().toString()+s.substring(j+k,i+1));
                j=i+1;
            }
            if(i==s.length()-1&&count<k&&count!=0) {
                res.append(new StringBuilder(s.substring(j,j+count)).reverse().toString());
            }
            if(i==s.length()-1&&count>=k) {
                res.append(new StringBuilder(s.substring(j,j+k)).reverse().toString()+s.substring(j+k,i+1));
            }
        }
        return res.toString();
    }
}  
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/reverse-string-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/reverse-string-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/reverse-string-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/reverse-string-ii/)

[回到目录](../README.md)