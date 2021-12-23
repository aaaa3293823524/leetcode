# 459. repeated-substring-pattern | 重复的子字符串

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abab&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> It is the substring &quot;ab&quot; twice.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aba&quot;
<strong>Output:</strong> false
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcabcabcabc&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> It is the substring &quot;abc&quot; four times or the substring &quot;abcabc&quot; twice.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
 instead-->
<p>给定一个非空的字符串，判断它是否可以由它的一个子串重复多次构成。给定的字符串只含有小写英文字母，并且长度不超过10000。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;abab&quot;

<strong>输出:</strong> True

<strong>解释:</strong> 可由子字符串 &quot;ab&quot; 重复两次构成。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> &quot;aba&quot;

<strong>输出:</strong> False
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> &quot;abcabcabcabc&quot;

<strong>输出:</strong> True

<strong>解释:</strong> 可由子字符串 &quot;abc&quot; 重复四次构成。 (或者子字符串 &quot;abcabc&quot; 重复两次构成。)
</pre>




## Solution

Language: **java**  /  Runtime: 15 ms

```java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        return kmp((s + s).substring(1,(s+s).length()-1), s);
    }

    public boolean kmp(String haystack, String needle) {
        // KMP算法：如果已经匹配的字符串包含相同的前缀和后缀，遇到下一个不匹配的位置时，指向needle的指针跳转到前缀的后一个位置，还是不匹配的话，再往前跳转后继续比较；先构造一个next数组来记录needle指针跳转的位置
        int n=haystack.length(), m=needle.length();
        if(m==0) return false;
        // 先构造next数组，next数组中的元素表示当前两个元素不匹配时，needle指针要跳转的位置
        // haystack: [a, b, e, a, b, a, b, e, a, b, f]
        // needle:   [a, b, e, a, b, f]
        // next:     [0, 0, 0, 1, 2, 0]
         int[] next = new int[m];
        for(int i=1,j=0; i<m; i++){
            while(j>0 && needle.charAt(i)!=needle.charAt(j)) 
                j = next[j-1]; // 一直和前一位置的值比较，直到遇到相等的字符或者j=0；j通过next[j-1]来回退
            if(needle.charAt(i)==needle.charAt(j)) j++;
            next[i] = j;
        }
        // 利用next数组进行跳转匹配，不再需要回退haystack的指针i
        for(int i=0,j=0; i<n; i++){
            // 匹配不成功，needle指针j回退并继续比较
            while(j>0 && haystack.charAt(i)!=needle.charAt(j))
                j = next[j-1];  
            if(haystack.charAt(i)==needle.charAt(j)) j++;
            if(j==m) return true;
        }
        return false;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/repeated-substring-pattern/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/repeated-substring-pattern/description/)

Solution: [LeetCode](https://leetcode.com/articles/repeated-substring-pattern/)  /  [LeetCode中国](https://leetcode-cn.com/articles/repeated-substring-pattern/)

[回到目录](../README.md)