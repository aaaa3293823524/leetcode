# 367. valid-perfect-square | 有效的完全平方数

## Question description

<!--If you want to use the English description, use <p>Given a <strong>positive</strong> integer <i>num</i>, write a function which returns True if <i>num</i> is a perfect square else False.</p>

<p><b>Follow up:</b> <b>Do not</b> use any built-in library function such as <code>sqrt</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> num = 16
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> num = 14
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= num &lt;= 2^31 - 1</code></li>
</ul>
 instead-->
<p>给定一个 <strong>正整数</strong> <code>num</code> ，编写一个函数，如果 <code>num</code> 是一个完全平方数，则返回 <code>true</code> ，否则返回 <code>false</code> 。</p>

<p><strong>进阶：不要</strong> 使用任何内置的库函数，如  <code>sqrt</code> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>num = 16
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>num = 14
<strong>输出：</strong>false
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= num <= 2^31 - 1</code></li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    bool isPerfectSquare(int num) {
        int i=1;
        while(num>0)
        {
            num-=i;
            i+=2;
        }
        return num==0;
    }
};


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/valid-perfect-square/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-perfect-square/description/)

Solution: [LeetCode](https://leetcode.com/articles/valid-perfect-square/)  /  [LeetCode中国](https://leetcode-cn.com/articles/valid-perfect-square/)

[回到目录](../README.md)