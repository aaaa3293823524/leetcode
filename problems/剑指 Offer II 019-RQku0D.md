# 剑指 Offer II 019. RQku0D | 最多删除一个字符得到回文

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个非空字符串&nbsp;<code>s</code>，请判断如果&nbsp;<strong>最多 </strong>从字符串中删除一个字符能否得到一个回文字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> s = &quot;aba&quot;
<strong>输出:</strong> true
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> s = &quot;abca&quot;
<strong>输出:</strong> true
<strong>解释:</strong> 可以删除 &quot;c&quot; 字符 或者 &quot;b&quot; 字符
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> s = &quot;abc&quot;
<strong>输出:</strong> false</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> 由小写英文字母组成</li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 680&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/valid-palindrome-ii/">https://leetcode-cn.com/problems/valid-palindrome-ii/</a></p>




## Solution

Language: **cpp**  /  Runtime: 40 ms

```cpp
class Solution {
public:
    bool validPalindrome(string s) {
        if (s.empty()) return true;

        int left = 0, right = s.length() - 1;
        while (s[left] == s[right] && left < right)     //把开头回文的部分先过掉
        {
            ++ left, -- right;
        }

        //如果直接过到一半的话，表示已经是回文串了
        //否则判断去除左边的一个字符或去除右边的一个字符后，剩下的字符串是否回文
        return left == s.length() / 2 || check(s, left + 1, right) || check(s, left, right - 1);
    }

    //判断在字符串s中，从left到right之间的子串是否回文
    bool check(string s, int left, int right)
    {
        while (left < right)
        {
            if (s[left] != s[right]) 
                break;
            ++ left, -- right;
        }

        return left >= right;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/RQku0D/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/RQku0D/description/)

Solution: [LeetCode](https://leetcode.com/articles/RQku0D/)  /  [LeetCode中国](https://leetcode-cn.com/articles/RQku0D/)

[回到目录](../README.md)