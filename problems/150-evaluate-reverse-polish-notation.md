# 150. evaluate-reverse-polish-notation | 逆波兰表达式求值

## Question description

<!--If you want to use the English description, use <p>Evaluate the value of an arithmetic expression in <a href="http://en.wikipedia.org/wiki/Reverse_Polish_notation" target="_blank">Reverse Polish Notation</a>.</p>

<p>Valid operators are <code>+</code>, <code>-</code>, <code>*</code>, and <code>/</code>. Each operand may be an integer or another expression.</p>

<p><strong>Note</strong> that division between two integers should truncate toward zero.</p>

<p>It is guaranteed that the given RPN expression is always valid. That means the expression would always evaluate to a result, and there will not be any division by zero operation.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> tokens = [&quot;2&quot;,&quot;1&quot;,&quot;+&quot;,&quot;3&quot;,&quot;*&quot;]
<strong>Output:</strong> 9
<strong>Explanation:</strong> ((2 + 1) * 3) = 9
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> tokens = [&quot;4&quot;,&quot;13&quot;,&quot;5&quot;,&quot;/&quot;,&quot;+&quot;]
<strong>Output:</strong> 6
<strong>Explanation:</strong> (4 + (13 / 5)) = 6
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> tokens = [&quot;10&quot;,&quot;6&quot;,&quot;9&quot;,&quot;3&quot;,&quot;+&quot;,&quot;-11&quot;,&quot;*&quot;,&quot;/&quot;,&quot;*&quot;,&quot;17&quot;,&quot;+&quot;,&quot;5&quot;,&quot;+&quot;]
<strong>Output:</strong> 22
<strong>Explanation:</strong> ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= tokens.length &lt;= 10<sup>4</sup></code></li>
	<li><code>tokens[i]</code> is either an operator: <code>&quot;+&quot;</code>, <code>&quot;-&quot;</code>, <code>&quot;*&quot;</code>, or <code>&quot;/&quot;</code>, or an integer in the range <code>[-200, 200]</code>.</li>
</ul>
 instead-->
<p>根据<a href="https://baike.baidu.com/item/%E9%80%86%E6%B3%A2%E5%85%B0%E5%BC%8F/128437" target="_blank"> 逆波兰表示法</a>，求表达式的值。</p>

<p>有效的算符包括 <code>+</code>、<code>-</code>、<code>*</code>、<code>/</code> 。每个运算对象可以是整数，也可以是另一个逆波兰表达式。</p>

<p> </p>

<p><strong>说明：</strong></p>

<ul>
	<li>整数除法只保留整数部分。</li>
	<li>给定逆波兰表达式总是有效的。换句话说，表达式总会得出有效数值且不存在除数为 0 的情况。</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>tokens = ["2","1","+","3","*"]
<strong>输出：</strong>9
<strong>解释：</strong>该算式转化为常见的中缀算术表达式为：((2 + 1) * 3) = 9
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>tokens = ["4","13","5","/","+"]
<strong>输出：</strong>6
<strong>解释：</strong>该算式转化为常见的中缀算术表达式为：(4 + (13 / 5)) = 6
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
<strong>输出：</strong>22
<strong>解释：</strong>
该算式转化为常见的中缀算术表达式为：
  ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= tokens.length <= 10<sup>4</sup></code></li>
	<li><code>tokens[i]</code> 要么是一个算符（<code>"+"</code>、<code>"-"</code>、<code>"*"</code> 或 <code>"/"</code>），要么是一个在范围 <code>[-200, 200]</code> 内的整数</li>
</ul>

<p> </p>

<p><strong>逆波兰表达式：</strong></p>

<p>逆波兰表达式是一种后缀表达式，所谓后缀就是指算符写在后面。</p>

<ul>
	<li>平常使用的算式则是一种中缀表达式，如 <code>( 1 + 2 ) * ( 3 + 4 )</code> 。</li>
	<li>该算式的逆波兰表达式写法为 <code>( ( 1 2 + ) ( 3 4 + ) * )</code> 。</li>
</ul>

<p>逆波兰表达式主要有以下两个优点：</p>

<ul>
	<li>去掉括号后表达式无歧义，上式即便写成 <code>1 2 + 3 4 + * </code>也可以依据次序计算出正确结果。</li>
	<li>适合用栈操作运算：遇到数字则入栈；遇到算符则取出栈顶两个数字进行计算，并将结果压入栈中。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 7 ms

```java
class Solution {
    public int evalRPN(String[] tokens) {
        Deque<Integer>stack=new LinkedList<Integer>();
        if(tokens.length==0)return 0;
        for(int i=0;i<tokens.length;i++) {
            String string=tokens[i];
            if(string.equals("+")) {
                int t2=stack.pop();
                int t1=stack.pop();
                stack.push(t1+t2);
                continue;
            }
            if(string.equals("-")) {
                int t2=stack.pop();
                int t1=stack.pop();
                stack.push(t1-t2);
                continue;
            }
            if(string.equals("*")) {
                int t2=stack.pop();
                int t1=stack.pop();
                stack.push(t1*t2);
                continue;
            }
            if(string.equals("/")) {
                int t2=stack.pop();
                int t1=stack.pop();
                stack.push(t1/t2);
                continue;
            }
            stack.push(Integer.valueOf(string));
        }
        return stack.pop();
    }
}
```

Language: **python3**  /  Runtime: 172 ms

```python3
class Solution(object):
    def evalRPN(self, tokens):
        """
        :type tokens: List[str]
        :rtype: int
        """
        stack = list()
        operations = {'+', '-', '*', '/'}
        
        for token in tokens:
            if token in operations:
                # 是操作符
                right = stack.pop()
                left = stack.pop()
                if token == '+':
                    tmp = left + right
                elif token == '-':
                    tmp = left - right
                elif token == '*':
                    tmp = left * right
                else:
                    if left * right >= 0:
                        tmp = left // right
                    else:
                        tmp = -(-left // right)
                    
                stack.append(tmp)
            else:
                # 不是操作符
                stack.append(int(token))
        
        return stack[0]


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/evaluate-reverse-polish-notation/description/)

Solution: [LeetCode](https://leetcode.com/articles/evaluate-reverse-polish-notation/)  /  [LeetCode中国](https://leetcode-cn.com/articles/evaluate-reverse-polish-notation/)

[回到目录](../README.md)