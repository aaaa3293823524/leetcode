# 1047. remove-all-adjacent-duplicates-in-string | 删除字符串中的所有相邻重复项

## Question description

<!--If you want to use the English description, use <p>You are given a string <code>s</code> consisting of lowercase English letters. A <strong>duplicate removal</strong> consists of choosing two <strong>adjacent</strong> and <strong>equal</strong> letters and removing them.</p>

<p>We repeatedly make <strong>duplicate removals</strong> on <code>s</code> until we no longer can.</p>

<p>Return <em>the final string after all such duplicate removals have been made</em>. It can be proven that the answer is <strong>unique</strong>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abbaca&quot;
<strong>Output:</strong> &quot;ca&quot;
<strong>Explanation:</strong> 
For example, in &quot;abbaca&quot; we could remove &quot;bb&quot; since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is &quot;aaca&quot;, of which only &quot;aa&quot; is possible, so the final string is &quot;ca&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;azxxzy&quot;
<strong>Output:</strong> &quot;ay&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>
 instead-->
<p>给出由小写字母组成的字符串&nbsp;<code>S</code>，<strong>重复项删除操作</strong>会选择两个相邻且相同的字母，并删除它们。</p>

<p>在 S 上反复执行重复项删除操作，直到无法继续删除。</p>

<p>在完成所有重复项删除操作后返回最终的字符串。答案保证唯一。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>&quot;abbaca&quot;
<strong>输出：</strong>&quot;ca&quot;
<strong>解释：</strong>
例如，在 &quot;abbaca&quot; 中，我们可以删除 &quot;bb&quot; 由于两字母相邻且相同，这是此时唯一可以执行删除操作的重复项。之后我们得到字符串 &quot;aaca&quot;，其中又只有 &quot;aa&quot; 可以执行重复项删除操作，所以最后的字符串为 &quot;ca&quot;。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= S.length &lt;= 20000</code></li>
	<li><code>S</code> 仅由小写英文字母组成。</li>
</ol>




## Solution

Language: **java**  /  Runtime: 454 ms

```java
class Solution {
    public String removeDuplicates(String S) {
        boolean flag=true;
        int len=S.length();
        String string=S;
        while(flag) {
        flag=false;
        for(int i=0;i<string.length()-1;i++) {
            if (string.charAt(i)==string.charAt(i+1)) {
                string=string.substring(0,i)+string.substring(i+2,string.length());
                flag=true;
            }
        }
        }
        return string;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/remove-all-adjacent-duplicates-in-string/description/)

Solution: [LeetCode](https://leetcode.com/articles/remove-all-adjacent-duplicates-in-string/)  /  [LeetCode中国](https://leetcode-cn.com/articles/remove-all-adjacent-duplicates-in-string/)

[回到目录](../README.md)