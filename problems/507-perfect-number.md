# 507. perfect-number | 完美数

## Question description

<!--If you want to use the English description, use <p>A <a href="https://en.wikipedia.org/wiki/Perfect_number" target="_blank"><strong>perfect number</strong></a> is a <strong>positive integer</strong> that is equal to the sum of its <strong>positive divisors</strong>, excluding the number itself. A <strong>divisor</strong> of an integer <code>x</code> is an integer that can divide <code>x</code> evenly.</p>

<p>Given an integer <code>n</code>, return <code>true</code><em> if </em><code>n</code><em> is a perfect number, otherwise return </em><code>false</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 28
<strong>Output:</strong> true
<strong>Explanation:</strong> 28 = 1 + 2 + 4 + 7 + 14
1, 2, 4, 7, and 14 are all divisors of 28.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 7
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num &lt;= 10<sup>8</sup></code></li>
</ul>
 instead-->
<p>对于一个&nbsp;<strong>正整数</strong>，如果它和除了它自身以外的所有 <strong>正因子</strong> 之和相等，我们称它为 「完美数」。</p>

<p>给定一个&nbsp;<strong>整数&nbsp;</strong><code>n</code>，&nbsp;如果是完美数，返回 <code>true</code>，否则返回 <code>false</code></p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>num = 28
<strong>输出：</strong>true
<strong>解释：</strong>28 = 1 + 2 + 4 + 7 + 14
1, 2, 4, 7, 和 14 是 28 的所有正因子。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>num = 6
<strong>输出：</strong>true
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>num = 496
<strong>输出：</strong>true
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>num = 8128
<strong>输出：</strong>true
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>num = 2
<strong>输出：</strong>false
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= num &lt;= 10<sup>8</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 13 ms

```java
class Solution {
    public boolean checkPerfectNumber(int num) {
        int sum=1;
        if(num==1)return false;
        for(int i=2;i<=(int)Math.sqrt(num);i++) {
            if(num%i==0) {
                sum+=i;
                sum+=(num/i);
                System.out.println(i);
                System.out.println(":"+num/i);
            }
        }
        return sum==num;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/perfect-number/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/perfect-number/description/)

Solution: [LeetCode](https://leetcode.com/articles/perfect-number/)  /  [LeetCode中国](https://leetcode-cn.com/articles/perfect-number/)

[回到目录](../README.md)