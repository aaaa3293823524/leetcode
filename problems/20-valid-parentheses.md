# 20. valid-parentheses | 有效的括号

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code> containing just the characters <code>&#39;(&#39;</code>, <code>&#39;)&#39;</code>, <code>&#39;{&#39;</code>, <code>&#39;}&#39;</code>, <code>&#39;[&#39;</code> and <code>&#39;]&#39;</code>, determine if the input string is valid.</p>

<p>An input string is valid if:</p>

<ol>
	<li>Open brackets must be closed by the same type of brackets.</li>
	<li>Open brackets must be closed in the correct order.</li>
</ol>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;()&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;()[]{}&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(]&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of parentheses only <code>&#39;()[]{}&#39;</code>.</li>
</ul>
 instead-->
<p>给定一个只包括 <code>'('</code>，<code>')'</code>，<code>'{'</code>，<code>'}'</code>，<code>'['</code>，<code>']'</code> 的字符串 <code>s</code> ，判断字符串是否有效。</p>

<p>有效字符串需满足：</p>

<ol>
	<li>左括号必须用相同类型的右括号闭合。</li>
	<li>左括号必须以正确的顺序闭合。</li>
</ol>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "()"
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "()[]{}"
<strong>输出：</strong>true
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "(]"
<strong>输出：</strong>false
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>s = "([)]"
<strong>输出：</strong>false
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>s = "{[]}"
<strong>输出：</strong>true</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 10<sup>4</sup></code></li>
	<li><code>s</code> 仅由括号 <code>'()[]{}'</code> 组成</li>
</ul>




## Solution

Language: **cpp**  /  Runtime: 0 ms

```cpp
class Solution {
public:

    bool isValid(string s) {
        stack<char>st;
        for(int i = 0;i<s.length();i++)
        {
            switch(s.at(i))
            {
                case '(':
                case '[':
                case '{':
                    st.push(s.at(i));
                    break;
                case ')':
                    if(st.empty()||st.top()!='(') return false;
                    st.pop(); break;
                case ']':
                    if(st.empty()||st.top()!='[') return false;
                    st.pop(); break;
                case '}':
                    if(st.empty()||st.top()!='{') return false;
                    st.pop(); break;
            }
        }
        return st.empty();
    }
};

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/valid-parentheses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/valid-parentheses/description/)

Solution: [LeetCode](https://leetcode.com/articles/valid-parentheses/)  /  [LeetCode中国](https://leetcode-cn.com/articles/valid-parentheses/)

[回到目录](../README.md)