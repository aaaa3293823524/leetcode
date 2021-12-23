# 397. integer-replacement | 整数替换

## Question description

<!--If you want to use the English description, use <p>Given a positive integer <code>n</code>,&nbsp;you can apply one of the following&nbsp;operations:</p>

<ol>
	<li>If <code>n</code> is even, replace <code>n</code> with <code>n / 2</code>.</li>
	<li>If <code>n</code> is odd, replace <code>n</code> with either <code>n + 1</code> or <code>n - 1</code>.</li>
</ol>

<p>Return <em>the minimum number of operations needed for <code>n</code> to become <code>1</code></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 8
<strong>Output:</strong> 3
<strong>Explanation:</strong> 8 -&gt; 4 -&gt; 2 -&gt; 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 7
<strong>Output:</strong> 4
<strong>Explanation: </strong>7 -&gt; 8 -&gt; 4 -&gt; 2 -&gt; 1
or 7 -&gt; 6 -&gt; 3 -&gt; 2 -&gt; 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 4
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给定一个正整数 <code>n</code> ，你可以做如下操作：</p>

<ol>
	<li>如果 <code>n</code><em> </em>是偶数，则用 <code>n / 2</code>替换 <code>n</code><em> </em>。</li>
	<li>如果 <code>n</code><em> </em>是奇数，则可以用 <code>n + 1</code>或<code>n - 1</code>替换 <code>n</code> 。</li>
</ol>

<p><code>n</code><em> </em>变为 <code>1</code> 所需的最小替换次数是多少？</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 8
<strong>输出：</strong>3
<strong>解释：</strong>8 -> 4 -> 2 -> 1
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 7
<strong>输出：</strong>4
<strong>解释：</strong>7 -> 8 -> 4 -> 2 -> 1
或 7 -> 6 -> 3 -> 2 -> 1
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>n = 4
<strong>输出：</strong>2
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= n <= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    Map<Integer, Integer> memo = new HashMap<Integer, Integer>();

    public int integerReplacement(int n) {
        if (n == 1) {
            return 0;
        }
        if (!memo.containsKey(n)) {
            if (n % 2 == 0) {
                memo.put(n, 1 + integerReplacement(n / 2));
            } else {
                memo.put(n, 2 + Math.min(integerReplacement(n / 2), integerReplacement(n / 2 + 1)));
            }
        }
        return memo.get(n);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/integer-replacement/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/integer-replacement/description/)

Solution: [LeetCode](https://leetcode.com/articles/integer-replacement/)  /  [LeetCode中国](https://leetcode-cn.com/articles/integer-replacement/)

[回到目录](../README.md)