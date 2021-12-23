# 剑指 Offer II 002. JFETK5 | 二进制加法

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定两个 01 字符串&nbsp;<code>a</code>&nbsp;和&nbsp;<code>b</code>&nbsp;，请计算它们的和，并以二进制字符串的形式输出。</p>

<p>输入为 <strong>非空 </strong>字符串且只包含数字&nbsp;<code>1</code>&nbsp;和&nbsp;<code>0</code>。</p>

<p>&nbsp;</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre>
<strong>输入:</strong> a = &quot;11&quot;, b = &quot;10&quot;
<strong>输出:</strong> &quot;101&quot;</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>
<strong>输入:</strong> a = &quot;1010&quot;, b = &quot;1011&quot;
<strong>输出:</strong> &quot;10101&quot;</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>每个字符串仅由字符 <code>&#39;0&#39;</code> 或 <code>&#39;1&#39;</code> 组成。</li>
	<li><code>1 &lt;= a.length, b.length &lt;= 10^4</code></li>
	<li>字符串如果不是 <code>&quot;0&quot;</code> ，就都不含前导零。</li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 67&nbsp;题相同：<a href="https://leetcode-cn.com/problems/add-binary/">https://leetcode-cn.com/problems/add-binary/</a></p>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public String addBinary(String a, String b) {
    StringBuilder res = new StringBuilder();
    int carry = 0;
    int l1 = a.length() - 1;
    int l2 = b.length() - 1;
    while (l1 >= 0 || l2 >= 0) {
        int x = l1 < 0 ? 0 : a.charAt(l1) - '0';
        int y = l2 < 0 ? 0 : b.charAt(l2) - '0';

        int sum = x + y + carry;
        res.append(sum % 2);
        carry = sum / 2;

        l1--;
        l2--;
    }
    if (carry != 0) res.append(carry);
    return res.reverse().toString();
}


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/JFETK5/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/JFETK5/description/)

Solution: [LeetCode](https://leetcode.com/articles/JFETK5/)  /  [LeetCode中国](https://leetcode-cn.com/articles/JFETK5/)

[回到目录](../README.md)