# 剑指 Offer II 085. IDBivT | 生成匹配的括号

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>正整数&nbsp;<code>n</code>&nbsp;代表生成括号的对数，请设计一个函数，用于能够生成所有可能的并且 <strong>有效的 </strong>括号组合。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 3
<strong>输出：</strong>[&quot;((()))&quot;,&quot;(()())&quot;,&quot;(())()&quot;,&quot;()(())&quot;,&quot;()()()&quot;]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 1
<strong>输出：</strong>[&quot;()&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 8</code></li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 22&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/generate-parentheses/">https://leetcode-cn.com/problems/generate-parentheses/</a></p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    List<String> ans = new ArrayList<String>();
    StringBuilder sb = new StringBuilder();
    public List<String> generateParenthesis(int n) {
        dfs(0, 0, n);
        return ans;
    }
    public void dfs(int l, int r, int n) { //分别代表当前左括号数、右括号数、题目要求的括号对数
        if (r > l || l > n || r > n) return; //右括号数量多于左括号、左/右括号数量超出，这些情况都是不符合的
        if (l == n && r == n) { //左右括号均达到数量要求
            ans.add(sb.toString()); //添加结果
            return;
        }
        //尝试添加左括号
        sb.append('(');
        dfs(l + 1, r, n);
        sb.deleteCharAt(sb.length() - 1);
        //尝试添加右括号
        sb.append(')');
        dfs(l, r + 1, n);
        sb.deleteCharAt(sb.length() - 1);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/IDBivT/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/IDBivT/description/)

Solution: [LeetCode](https://leetcode.com/articles/IDBivT/)  /  [LeetCode中国](https://leetcode-cn.com/articles/IDBivT/)

[回到目录](../README.md)