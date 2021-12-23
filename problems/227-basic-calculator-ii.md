# 227. basic-calculator-ii | 基本计算器 II

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code> which represents an expression, <em>evaluate this expression and return its value</em>.&nbsp;</p>

<p>The integer division should truncate toward zero.</p>

<p>You may assume that the given expression is always valid. All intermediate results will be in the range of <code>[-2<sup>31</sup>, 2<sup>31</sup> - 1]</code>.</p>

<p><strong>Note:</strong> You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as <code>eval()</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> s = "3+2*2"
<strong>Output:</strong> 7
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> s = " 3/2 "
<strong>Output:</strong> 1
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> s = " 3+5 / 2 "
<strong>Output:</strong> 5
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 3 * 10<sup>5</sup></code></li>
	<li><code>s</code> consists of integers and operators <code>(&#39;+&#39;, &#39;-&#39;, &#39;*&#39;, &#39;/&#39;)</code> separated by some number of spaces.</li>
	<li><code>s</code> represents <strong>a valid expression</strong>.</li>
	<li>All the integers in the expression are non-negative integers in the range <code>[0, 2<sup>31</sup> - 1]</code>.</li>
	<li>The answer is <strong>guaranteed</strong> to fit in a <strong>32-bit integer</strong>.</li>
</ul>
 instead-->
<p>给你一个字符串表达式 <code>s</code> ，请你实现一个基本计算器来计算并返回它的值。</p>

<p>整数除法仅保留整数部分。</p>

<div class="original__bRMd">
<div>
<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "3+2*2"
<strong>输出：</strong>7
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = " 3/2 "
<strong>输出：</strong>1
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = " 3+5 / 2 "
<strong>输出：</strong>5
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 3 * 10<sup>5</sup></code></li>
	<li><code>s</code> 由整数和算符 <code>('+', '-', '*', '/')</code> 组成，中间由一些空格隔开</li>
	<li><code>s</code> 表示一个 <strong>有效表达式</strong></li>
	<li>表达式中的所有整数都是非负整数，且在范围 <code>[0, 2<sup>31</sup> - 1]</code> 内</li>
	<li>题目数据保证答案是一个 <strong>32-bit 整数</strong></li>
</ul>
</div>
</div>




## Solution

Language: **java**  /  Runtime: 173 ms

```java
class Solution {
    public int calculate(String s) {
        Deque<Integer> stack = new LinkedList<Integer>();
        char preSign = '+';
        int num = 0;
        int n = s.length();
        for (int i = 0; i < n; ++i) {
            if (Character.isDigit(s.charAt(i))) {
                num = num * 10 + s.charAt(i) - '0';
            }
            if (!Character.isDigit(s.charAt(i)) && s.charAt(i) != ' ' || i == n - 1) {
                switch (preSign) {
                    case '+':
                        stack.push(num);
                        break;
                    case '-':
                        stack.push(-num);
                        break;
                    case '*':
                        stack.push(stack.pop() * num);
                        break;
                    default:
                        stack.push(stack.pop() / num);
                }
                preSign = s.charAt(i);
                System.out.println(preSign);
                num = 0;
            }
        }
        int ans = 0;
        while (!stack.isEmpty()) {
            ans += stack.pop();
        }
        return ans;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/basic-calculator-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/basic-calculator-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/basic-calculator-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/basic-calculator-ii/)

[回到目录](../README.md)