# 415. add-strings | 字符串相加

## Question description

<!--If you want to use the English description, use <p>Given two non-negative integers, <code>num1</code> and <code>num2</code> represented as string, return <em>the sum of</em> <code>num1</code> <em>and</em> <code>num2</code> <em>as a string</em>.</p>

<p>You must solve the problem without using any built-in library for handling large integers (such as <code>BigInteger</code>). You must also not convert the inputs to integers directly.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> num1 = &quot;11&quot;, num2 = &quot;123&quot;
<strong>Output:</strong> &quot;134&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> num1 = &quot;456&quot;, num2 = &quot;77&quot;
<strong>Output:</strong> &quot;533&quot;
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> num1 = &quot;0&quot;, num2 = &quot;0&quot;
<strong>Output:</strong> &quot;0&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num1.length, num2.length &lt;= 10<sup>4</sup></code></li>
	<li><code>num1</code> and <code>num2</code> consist of only digits.</li>
	<li><code>num1</code> and <code>num2</code> don&#39;t have any leading zeros except for the zero itself.</li>
</ul>
 instead-->
<p>给定两个字符串形式的非负整数&nbsp;<code>num1</code> 和<code>num2</code>&nbsp;，计算它们的和并同样以字符串形式返回。</p>

<p>你不能使用任何內建的用于处理大整数的库（比如 <code>BigInteger</code>），&nbsp;也不能直接将输入的字符串转换为整数形式。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>num1 = "11", num2 = "123"
<strong>输出：</strong>"134"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>num1 = "456", num2 = "77"
<strong>输出：</strong>"533"
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>num1 = "0", num2 = "0"
<strong>输出：</strong>"0"
</pre>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= num1.length, num2.length &lt;= 10<sup>4</sup></code></li>
	<li><code>num1</code> 和<code>num2</code> 都只包含数字&nbsp;<code>0-9</code></li>
	<li><code>num1</code> 和<code>num2</code> 都不包含任何前导零</li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public String addStrings(String num1, String num2) {
        int i = num1.length() - 1, j = num2.length() - 1, add = 0;
        StringBuffer ans = new StringBuffer();
        while (i >= 0 || j >= 0 || add != 0) {
            int x = i >= 0 ? num1.charAt(i) - '0' : 0;
            int y = j >= 0 ? num2.charAt(j) - '0' : 0;
            int result = x + y + add;
            ans.append(result % 10);
            add = result / 10;
            i--;
            j--;
        }
        // 计算完以后的答案需要翻转过来
        ans.reverse();
        return ans.toString();
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/add-strings/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/add-strings/description/)

Solution: [LeetCode](https://leetcode.com/articles/add-strings/)  /  [LeetCode中国](https://leetcode-cn.com/articles/add-strings/)

[回到目录](../README.md)