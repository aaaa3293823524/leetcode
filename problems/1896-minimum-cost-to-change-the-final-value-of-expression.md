﻿# 1896. minimum-cost-to-change-the-final-value-of-expression | 反转表达式值的最少操作次数

## Question description

<!--If you want to use the English description, use <p>You are given a <strong>valid</strong> boolean expression as a string <code>expression</code> consisting of the characters <code>&#39;1&#39;</code>,<code>&#39;0&#39;</code>,<code>&#39;&amp;&#39;</code> (bitwise <strong>AND</strong> operator),<code>&#39;|&#39;</code> (bitwise <strong>OR</strong> operator),<code>&#39;(&#39;</code>, and <code>&#39;)&#39;</code>.</p>

<ul>
	<li>For example, <code>&quot;()1|1&quot;</code> and <code>&quot;(1)&amp;()&quot;</code> are <strong>not valid</strong> while <code>&quot;1&quot;</code>, <code>&quot;(((1))|(0))&quot;</code>, and <code>&quot;1|(0&amp;(1))&quot;</code> are <strong>valid</strong> expressions.</li>
</ul>

<p>Return<em> the <strong>minimum cost</strong> to change the final value of the expression</em>.</p>

<ul>
	<li>For example, if <code>expression = &quot;1|1|(0&amp;0)&amp;1&quot;</code>, its <strong>value</strong> is <code>1|1|(0&amp;0)&amp;1 = 1|1|0&amp;1 = 1|0&amp;1 = 1&amp;1 = 1</code>. We want to apply operations so that the<strong> new</strong> expression evaluates to <code>0</code>.</li>
</ul>

<p>The <strong>cost</strong> of changing the final value of an expression is the <strong>number of operations</strong> performed on the expression. The types of <strong>operations</strong> are described as follows:</p>

<ul>
	<li>Turn a <code>&#39;1&#39;</code> into a <code>&#39;0&#39;</code>.</li>
	<li>Turn a <code>&#39;0&#39;</code> into a <code>&#39;1&#39;</code>.</li>
	<li>Turn a <code>&#39;&amp;&#39;</code> into a <code>&#39;|&#39;</code>.</li>
	<li>Turn a <code>&#39;|&#39;</code> into a <code>&#39;&amp;&#39;</code>.</li>
</ul>

<p><strong>Note:</strong> <code>&#39;&amp;&#39;</code> does <strong>not</strong> take precedence over <code>&#39;|&#39;</code> in the <strong>order of calculation</strong>. Evaluate parentheses <strong>first</strong>, then in <strong>left-to-right</strong> order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> expression = &quot;1&amp;(0|1)&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> We can turn &quot;1&amp;(0<u><strong>|</strong></u>1)&quot; into &quot;1&amp;(0<u><strong>&amp;</strong></u>1)&quot; by changing the &#39;|&#39; to a &#39;&amp;&#39; using 1 operation.
The new expression evaluates to 0. 
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> expression = &quot;(0&amp;0)&amp;(0&amp;0&amp;0)&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> We can turn &quot;(0<u><strong>&amp;0</strong></u>)<strong><u>&amp;</u></strong>(0&amp;0&amp;0)&quot; into &quot;(0<u><strong>|1</strong></u>)<u><strong>|</strong></u>(0&amp;0&amp;0)&quot; using 3 operations.
The new expression evaluates to 1.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> expression = &quot;(0|(1|0&amp;1))&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> We can turn &quot;(0|(<u><strong>1</strong></u>|0&amp;1))&quot; into &quot;(0|(<u><strong>0</strong></u>|0&amp;1))&quot; using 1 operation.
The new expression evaluates to 0.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= expression.length &lt;= 10<sup>5</sup></code></li>
	<li><code>expression</code>&nbsp;only contains&nbsp;<code>&#39;1&#39;</code>,<code>&#39;0&#39;</code>,<code>&#39;&amp;&#39;</code>,<code>&#39;|&#39;</code>,<code>&#39;(&#39;</code>, and&nbsp;<code>&#39;)&#39;</code></li>
	<li>All parentheses&nbsp;are properly matched.</li>
	<li>There will be no empty parentheses (i.e:&nbsp;<code>&quot;()&quot;</code>&nbsp;is not a substring of&nbsp;<code>expression</code>).</li>
</ul>
 instead-->
<p>给你一个 <strong>有效的</strong> 布尔表达式，用字符串 <code>expression</code> 表示。这个字符串包含字符 <code>'1'</code>，<code>'0'</code>，<code>'&amp;'</code>（按位 <strong>与</strong> 运算），<code>'|'</code>（按位 <strong>或</strong> 运算），<code>'('</code> 和 <code>')'</code> 。</p>

<ul>
	<li>比方说，<code>"()1|1"</code> 和 <code>"(1)&amp;()"</code> <strong>不是有效</strong> 布尔表达式。而 <code>"1"</code>， <code>"(((1))|(0))"</code> 和 <code>"1|(0&amp;(1))"</code> 是 <strong>有效</strong> 布尔表达式。</li>
</ul>

<p>你的目标是将布尔表达式的 <strong>值</strong> <strong>反转 </strong>（也就是将 <code>0</code> 变为 <code>1</code> ，或者将 <code>1</code> 变为 <code>0</code>），请你返回达成目标需要的 <strong>最少操作</strong> 次数。</p>

<ul>
	<li>比方说，如果表达式 <code>expression = "1|1|(0&amp;0)&amp;1"</code> ，它的 <strong>值</strong> 为 <code>1|1|(0&amp;0)&amp;1 = 1|1|0&amp;1 = 1|0&amp;1 = 1&amp;1 = 1</code> 。我们想要执行操作将 <strong>新的</strong> 表达式的值变成 <code>0</code> 。</li>
</ul>

<p>可执行的 <strong>操作</strong> 如下：</p>

<ul>
	<li>将一个 <code>'1'</code> 变成一个 <code>'0'</code> 。</li>
	<li>将一个 <code>'0'</code> 变成一个 <code>'1'</code> 。</li>
	<li>将一个 <code>'&amp;'</code> 变成一个 <code>'|'</code> 。</li>
	<li>将一个 <code>'|'</code> 变成一个 <code>'&amp;'</code> 。</li>
</ul>

<p><strong>注意：</strong><code>'&amp;'</code> 的 <strong>运算优先级</strong> 与 <code>'|'</code> <strong>相同</strong> 。计算表达式时，括号优先级 <strong>最高</strong> ，然后按照 <strong>从左到右</strong> 的顺序运算。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>expression = "1&amp;(0|1)"
<b>输出：</b>1
<b>解释：</b>我们可以将 "1&amp;(0<strong>|</strong>1)" 变成 "1&amp;(0<strong>&amp;</strong>1)" ，执行的操作为将一个 '|' 变成一个 '&amp;' ，执行了 1 次操作。
新表达式的值为 0 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>expression = "(0&amp;0)&amp;(0&amp;0&amp;0)"
<b>输出：</b>3
<b>解释：</b>我们可以将 "(0<strong>&amp;0</strong>)<strong>&amp;</strong>(0&amp;0&amp;0)" 变成 "(0<strong>|1</strong>)<strong>|</strong>(0&amp;0&amp;0)" ，执行了 3 次操作。
新表达式的值为 1 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>expression = "(0|(1|0&amp;1))"
<b>输出：</b>1
<b>解释：</b>我们可以将 "(0|(<strong>1</strong>|0&amp;1))" 变成 "(0|(<strong>0</strong>|0&amp;1))" ，执行了 1 次操作。
新表达式的值为 0 。</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= expression.length &lt;= 10<sup>5</sup></code></li>
	<li><code>expression</code> 只包含 <code>'1'</code>，<code>'0'</code>，<code>'&amp;'</code>，<code>'|'</code>，<code>'('</code> 和 <code>')'</code></li>
	<li>所有括号都有与之匹配的对应括号。</li>
	<li>不会有空的括号（也就是说 <code>"()"</code> 不是 <code>expression</code> 的子字符串）。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 40 ms

```java
class Solution {
    public int minOperationsToFlip(String expression) {
        char[] exp = expression.toCharArray();//转为char[]简化代码
        Deque<Integer> num = new LinkedList<>();//栈，存储当前表达式的结果值
        Deque<Integer> op = new LinkedList<>();//栈，存储反转当前表达式的最小操作次数，与表达式结果栈中的元素一一对应（二者也可合并为一个存储了对应数组的栈）
        Deque<Character> sign = new LinkedList<>();//符号栈
        for (char e : exp) {
            if (e == '(' || e == '&' || e == '|') {//除')'以外的符号直接入栈
                sign.offerFirst(e);
                continue;
            } else if (e == ')') {//遇到右括号，弹出上一左括号，触发后续计算
                sign.pollFirst();
            } else {//遇到数字，入栈
                num.offerFirst((int)(e - '0'));//数值
                op.offerFirst(1);//任意单个数值反转操作次数为1
            }
            //计算当前可处理的表达式部分
            if (num.size() > 1 && sign.peekFirst() != '(') {//栈中存在超过2个数字，且未被括号分隔，可处理
                int[] result = minOp(num.pollFirst(), num.pollFirst(), op.pollFirst(), op.pollFirst(), sign.pollFirst());//计算当前表达式的值和最小反转操作次数
                num.offerFirst(result[0]);
                op.offerFirst(result[1]);
            }
        }
        return op.peekFirst();//反转操作次数栈此时只剩1个元素，就是整个表达式反转的最小操作次数
    }

    //针对计算当前表达式中的2个元素，计算值和最小反转操作次数
    public int[] minOp(int num1, int num2, int op1, int op2, char sign) {
        if (sign == '&') {
            if (num1 == 1 && num2 == 1)//1&1,将其中一个1反转为0
                return new int[]{1, Math.min(op1, op2)};
            else if (num1 == 0 && num2 == 0)//0&0,将其中一个0反转为1,并将&反转为|
                return new int[]{0, Math.min(op1, op2) + 1};
            else//1&0,将&反转为|
                return new int[]{0, 1};
        } else {
            if (num1 == 0 && num2 == 0)//0|0，将其中一个0反转为1
                return new int[]{0, Math.min(op1, op2)};
            else if (num1 == 1 && num2 == 1)//1|1,将其中一个1反转为0，并将|反转为&
                return new int[]{1, Math.min(op1, op2) + 1};
            else//1|0,将|反转为&
                return new int[]{1, 1};
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-cost-to-change-the-final-value-of-expression/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-cost-to-change-the-final-value-of-expression/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-cost-to-change-the-final-value-of-expression/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-cost-to-change-the-final-value-of-expression/)

[回到目录](../README.md)