﻿# 剑指 Offer 58 - II. zuo-xuan-zhuan-zi-fu-chuan-lcof | 左旋转字符串

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串&quot;abcdefg&quot;和数字2，该函数将返回左旋转两位得到的结果&quot;cdefgab&quot;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入:</strong> s = &quot;abcdefg&quot;, k = 2
<strong>输出:&nbsp;</strong>&quot;cdefgab&quot;
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入:</strong> s = &quot;lrloseumgh&quot;, k = 6
<strong>输出:&nbsp;</strong>&quot;umghlrlose&quot;
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>1 &lt;= k &lt; s.length &lt;= 10000</code></li>
</ul>




## Solution

Language: **python3**  /  Runtime: 32 ms

```python3
class Solution:
    def reverseLeftWords(self, s: str, n: int) -> str:
        return s[n:]+s[:n]
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/zuo-xuan-zhuan-zi-fu-chuan-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/zuo-xuan-zhuan-zi-fu-chuan-lcof/)

[回到目录](../README.md)