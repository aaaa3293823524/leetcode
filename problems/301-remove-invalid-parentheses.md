# 301. remove-invalid-parentheses | 删除无效的括号

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code> that contains parentheses and letters, remove the minimum number of invalid parentheses to make the input string valid.</p>

<p>Return <em>all the possible results</em>. You may return the answer in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;()())()&quot;
<strong>Output:</strong> [&quot;(())()&quot;,&quot;()()()&quot;]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(a)())()&quot;
<strong>Output:</strong> [&quot;(a())()&quot;,&quot;(a)()()&quot;]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;)(&quot;
<strong>Output:</strong> [&quot;&quot;]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 25</code></li>
	<li><code>s</code> consists of lowercase English letters and parentheses <code>&#39;(&#39;</code> and <code>&#39;)&#39;</code>.</li>
	<li>There will be at most <code>20</code> parentheses in <code>s</code>.</li>
</ul>
 instead-->
<p>给你一个由若干括号和字母组成的字符串 <code>s</code> ，删除最小数量的无效括号，使得输入的字符串有效。</p>

<p>返回所有可能的结果。答案可以按 <strong>任意顺序</strong> 返回。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "()())()"
<strong>输出：</strong>["(())()","()()()"]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "(a)())()"
<strong>输出：</strong>["(a())()","(a)()()"]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = ")("
<strong>输出：</strong>[""]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 25</code></li>
	<li><code>s</code> 由小写英文字母以及括号 <code>'('</code> 和 <code>')'</code> 组成</li>
	<li><code>s</code> 中至多含 <code>20</code> 个括号</li>
</ul>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    private List<String> res = new ArrayList<String>();

    public List<String> removeInvalidParentheses(String s) {
        int lremove = 0;
        int rremove = 0;

        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') {
                lremove++;
            } else if (s.charAt(i) == ')') {
                if (lremove == 0) {
                    rremove++;
                } else {
                    lremove--;
                }
            }
        }
        helper(s, 0, lremove, rremove);

        return res;
    }

    private void helper(String str, int start, int lremove, int rremove) {
        if (lremove == 0 && rremove == 0) {
            if (isValid(str)) {
                res.add(str);
            }
            return;
        }

        for (int i = start; i < str.length(); i++) {   //从不同位置去掉括号
            if (i != start && str.charAt(i) == str.charAt(i - 1)) {
                continue;
            }
            // 如果剩余的字符无法满足去掉的数量要求，直接返回
            if (lremove + rremove > str.length() - i) {
                return;
            }
            // 尝试去掉一个左括号
            if (lremove > 0 && str.charAt(i) == '(') {
                helper(str.substring(0, i) + str.substring(i + 1), i, lremove - 1, rremove);
            }
            // 尝试去掉一个右括号
            if (rremove > 0 && str.charAt(i) == ')') {
                helper(str.substring(0, i) + str.substring(i + 1), i, lremove, rremove - 1);
            }
        }
        
    }

    private boolean isValid(String str) {
        int cnt = 0;
        for (int i = 0; i < str.length(); i++) {
            if (str.charAt(i) == '(') {
                cnt++;
            } else if (str.charAt(i) == ')') {
                cnt--;
                if (cnt < 0) {
                    return false;
                }
            }
        }

        return cnt == 0;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/remove-invalid-parentheses/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-invalid-parentheses/description/)

Solution: [LeetCode](https://leetcode.com/articles/remove-invalid-parentheses/)  /  [LeetCode中国](https://leetcode-cn.com/articles/remove-invalid-parentheses/)

[回到目录](../README.md)