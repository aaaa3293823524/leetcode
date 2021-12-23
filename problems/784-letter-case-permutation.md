# 784. letter-case-permutation | 字母大小写全排列

## Question description

<!--If you want to use the English description, use <p>Given a string <code>s</code>, you&nbsp;can transform every letter individually to be lowercase or uppercase to create another string.</p>

<p>Return <em>a list of all possible strings we could create</em>. Return the output in <strong>any order</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;a1b2&quot;
<strong>Output:</strong> [&quot;a1b2&quot;,&quot;a1B2&quot;,&quot;A1b2&quot;,&quot;A1B2&quot;]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;3z4&quot;
<strong>Output:</strong> [&quot;3z4&quot;,&quot;3Z4&quot;]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 12</code></li>
	<li><code>s</code> consists of lowercase English letters, uppercase English letters, and digits.</li>
</ul>
 instead-->
<p>给定一个字符串<code>S</code>，通过将字符串<code>S</code>中的每个字母转变大小写，我们可以获得一个新的字符串。返回所有可能得到的字符串集合。</p>

<p>&nbsp;</p>

<pre><strong>示例：</strong>
<strong>输入：</strong>S = &quot;a1b2&quot;
<strong>输出：</strong>[&quot;a1b2&quot;, &quot;a1B2&quot;, &quot;A1b2&quot;, &quot;A1B2&quot;]

<strong>输入：</strong>S = &quot;3z4&quot;
<strong>输出：</strong>[&quot;3z4&quot;, &quot;3Z4&quot;]

<strong>输入：</strong>S = &quot;12345&quot;
<strong>输出：</strong>[&quot;12345&quot;]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>S</code>&nbsp;的长度不超过<code>12</code>。</li>
	<li><code>S</code>&nbsp;仅由数字和字母组成。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    List<String> res = new ArrayList<>();
    public List<String> letterCasePermutation(String S) {
        char[] chs = S.toCharArray();
        int n = chs.length;
        dfs(chs, n, 0);
        return res;
    }

    private void dfs(char[] chs, int n, int begin) {
        res.add(new String(chs));
        for(int i = begin; i < n; i++){
            if(!Character.isDigit(chs[i])){
                char tmp = chs[i];
                chs[i] = (char)(chs[i] - 'a' >= 0 ? chs[i] - 32 : chs[i] + 32);
                dfs(chs, n, i + 1);
                chs[i] = tmp;
            }
        }
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/letter-case-permutation/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/letter-case-permutation/description/)

Solution: [LeetCode](https://leetcode.com/articles/letter-case-permutation/)  /  [LeetCode中国](https://leetcode-cn.com/articles/letter-case-permutation/)

[回到目录](../README.md)