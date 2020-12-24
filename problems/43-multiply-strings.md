# 43. multiply-strings | 字符串相乘

## Question description

<!--If you want to use the English description, use <p>Given two non-negative integers <code>num1</code> and <code>num2</code> represented as strings, return the product of <code>num1</code> and <code>num2</code>, also represented as a string.</p>

<p><strong>Note:</strong>&nbsp;You must not use any built-in BigInteger library or convert the inputs to integer directly.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> num1 = "2", num2 = "3"
<strong>Output:</strong> "6"
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> num1 = "123", num2 = "456"
<strong>Output:</strong> "56088"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num1.length, num2.length &lt;= 200</code></li>
	<li><code>num1</code> and <code>num2</code> consist of digits only.</li>
	<li>Both <code>num1</code> and <code>num2</code>&nbsp;do not contain any leading zero, except the number <code>0</code> itself.</li>
</ul>
 instead-->
<p>给定两个以字符串形式表示的非负整数&nbsp;<code>num1</code>&nbsp;和&nbsp;<code>num2</code>，返回&nbsp;<code>num1</code>&nbsp;和&nbsp;<code>num2</code>&nbsp;的乘积，它们的乘积也表示为字符串形式。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> num1 = &quot;2&quot;, num2 = &quot;3&quot;
<strong>输出:</strong> &quot;6&quot;</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> num1 = &quot;123&quot;, num2 = &quot;456&quot;
<strong>输出:</strong> &quot;56088&quot;</pre>

<p><strong>说明：</strong></p>

<ol>
	<li><code>num1</code>&nbsp;和&nbsp;<code>num2</code>&nbsp;的长度小于110。</li>
	<li><code>num1</code> 和&nbsp;<code>num2</code> 只包含数字&nbsp;<code>0-9</code>。</li>
	<li><code>num1</code> 和&nbsp;<code>num2</code>&nbsp;均不以零开头，除非是数字 0 本身。</li>
	<li><strong>不能使用任何标准库的大数类型（比如 BigInteger）</strong>或<strong>直接将输入转换为整数来处理</strong>。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 82 ms

```java
class Solution {
    public String multiply(String num1, String num2) {
        if (num1.equals("0") || num2.equals("0"))
            return "0";

        int len1 = num1.length(), len2 = num2.length();
        int[][] arr = new int[len2][len1 + len2];
        int pos = 0; // 决定存储哪一行位置的pos
        for (int j = len2 - 1; j >= 0; j--) {
            StringBuilder s = new StringBuilder();
            int temp = 0;
            for (int i = len1 - 1; i >= 0; i--) {
                temp += (num1.charAt(i) - '0') * (num2.charAt(j) - '0');
                s.append(temp % 10);
                temp /= 10;
            }
            if (temp != 0)
                s.append(temp);
            int k = 0;
            int index = arr[0].length - 1 - pos;// index 决定从后面倒数第几个位置开始存储
            while (k < s.length()) {
                arr[pos][index--] = s.charAt(k) - '0';
                k++;
            }
            pos++;
        }
        StringBuilder s = new StringBuilder();// 存储反转的结果值
        int temp = 0;
        for (int k = arr[0].length - 1; k >= 0; k--) {
            for (int i = 0; i < arr.length; i++) {
                temp += arr[i][k];
            }
            s.append(temp % 10);
            temp /= 10;
        }
        String res = s.reverse().toString();// 将结果值反转,并且去掉前面多余的 0 即可
        int i = 0;
        while (res.charAt(i) == '0')
            i++;
        return res.substring(i); // 截取不带前缀 0 的子串
    }

}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/multiply-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/multiply-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/multiply-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/multiply-strings/)

[回到目录](../README.md)