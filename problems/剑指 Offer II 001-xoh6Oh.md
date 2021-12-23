# 剑指 Offer II 001. xoh6Oh | 整数除法

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p> instead-->
<p>给定两个整数 <code>a</code> 和 <code>b</code> ，求它们的除法的商 <code>a/b</code> ，要求不得使用乘号 <code>&#39;*&#39;</code>、除号 <code>&#39;/&#39;</code> 以及求余符号 <code>&#39;%&#39;</code>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>注意：</strong></p>

<ul>
	<li>整数除法的结果应当截去（<code>truncate</code>）其小数部分，例如：<code>truncate(8.345) = 8</code>&nbsp;以及&nbsp;<code>truncate(-2.7335) = -2</code></li>
	<li>假设我们的环境只能存储 32 位有符号整数，其数值范围是 <code>[&minus;2<sup>31</sup>,&nbsp;2<sup>31</sup>&minus;1]</code>。本题中，如果除法结果溢出，则返回 <code>2<sup>31&nbsp;</sup>&minus; 1</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>a = 15, b = 2
<strong>输出：</strong>7
<strong><span style="white-space: pre-wrap;">解释：</span></strong>15/2 = truncate(7.5) = 7
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>a = 7, b = -3
<strong>输出：</strong><span style="white-space: pre-wrap;">-2</span>
<strong><span style="white-space: pre-wrap;">解释：</span></strong>7/-3 = truncate(-2.33333..) = -2</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>a = 0, b = 1
<strong>输出：</strong><span style="white-space: pre-wrap;">0</span></pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>a = 1, b = 1
<strong>输出：</strong><span style="white-space: pre-wrap;">1</span></pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>-2<sup>31</sup>&nbsp;&lt;= a, b &lt;= 2<sup>31</sup>&nbsp;- 1</code></li>
	<li><code>b != 0</code></li>
</ul>

<p>&nbsp;</p>

<p>注意：本题与主站 29&nbsp;题相同：<a href="https://leetcode-cn.com/problems/divide-two-integers/">https://leetcode-cn.com/problems/divide-two-integers/</a></p>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int divide(int a, int b) {
        long na = a, nb = b;
        na = Math.abs(na);
        nb = Math.abs(nb);
        char[] chars = String.valueOf(na).toCharArray();
        long c;
        StringBuffer build = new StringBuffer();
        StringBuilder res = new StringBuilder(0);
        for (int i = 0; i < chars.length; i++) {
            c = Long.valueOf(build.append(chars[i] - '0').toString());
            if(c >= nb) {
                res.append(sub(c, nb, build));
            } else if (i != 0) {
                res.append(0);
            }
        }
        long ans = Long.valueOf(0 + res.toString());
        if((a < 0 && b > 0) || (a > 0 && b < 0)) {
            ans = -ans;
        }
        if(ans > Integer.MAX_VALUE) {
            ans -= 1;
        }
        return (int)ans;
    }

    private int sub(long sum, long base, StringBuffer build){
        long summarise = sum;
        int cnt = 0;
        while (summarise >= base) {
            summarise -= base;
            cnt++;
        }
        build.replace(0, build.length(),"");
        build.append(summarise);
        return cnt;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/xoh6Oh/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/xoh6Oh/description/)

Solution: [LeetCode](https://leetcode.com/articles/xoh6Oh/)  /  [LeetCode中国](https://leetcode-cn.com/articles/xoh6Oh/)

[回到目录](../README.md)