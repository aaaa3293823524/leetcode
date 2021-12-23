# 66. plus-one | 加一

## Question description

<!--If you want to use the English description, use <p>You are given a <strong>large integer</strong> represented as an integer array <code>digits</code>, where each <code>digits[i]</code> is the <code>i<sup>th</sup></code> digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading <code>0</code>&#39;s.</p>

<p>Increment the large integer by one and return <em>the resulting array of digits</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> digits = [1,2,3]
<strong>Output:</strong> [1,2,4]
<strong>Explanation:</strong> The array represents the integer 123.
Incrementing by one gives 123 + 1 = 124.
Thus, the result should be [1,2,4].
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> digits = [4,3,2,1]
<strong>Output:</strong> [4,3,2,2]
<strong>Explanation:</strong> The array represents the integer 4321.
Incrementing by one gives 4321 + 1 = 4322.
Thus, the result should be [4,3,2,2].
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> digits = [9]
<strong>Output:</strong> [1,0]
<strong>Explanation:</strong> The array represents the integer 9.
Incrementing by one gives 9 + 1 = 10.
Thus, the result should be [1,0].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= digits.length &lt;= 100</code></li>
	<li><code>0 &lt;= digits[i] &lt;= 9</code></li>
	<li><code>digits</code> does not contain any leading <code>0</code>&#39;s.</li>
</ul>
 instead-->
<p>给定一个由 <strong>整数 </strong>组成的<strong> 非空</strong> 数组所表示的非负整数，在该数的基础上加一。</p>

<p>最高位数字存放在数组的首位， 数组中每个元素只存储<strong>单个</strong>数字。</p>

<p>你可以假设除了整数 0 之外，这个整数不会以零开头。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>digits = [1,2,3]
<strong>输出：</strong>[1,2,4]
<strong>解释：</strong>输入数组表示数字 123。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>digits = [4,3,2,1]
<strong>输出：</strong>[4,3,2,2]
<strong>解释：</strong>输入数组表示数字 4321。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>digits = [0]
<strong>输出：</strong>[1]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= digits.length <= 100</code></li>
	<li><code>0 <= digits[i] <= 9</code></li>
</ul>




## Solution

Language: **python3**  /  Runtime: 64 ms

```python3
class Solution:
    def plusOne(self, digits):
        digits=digits[::-1]
        d=[]

        sum = digits[0] + 1
        carry = sum // 10
        d.append(sum%10)
        for i in digits[1:]:
            sum=i+carry
            carry=sum//10
            d.append(sum%10)
        if(carry!=0):
            d.append(carry)
        return d[::-1]
        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/plus-one/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/plus-one/description/)

Solution: [LeetCode](https://leetcode.com/articles/plus-one/)  /  [LeetCode中国](https://leetcode-cn.com/articles/plus-one/)

[回到目录](../README.md)