# 1987. number-of-unique-good-subsequences | 不同的好子序列数目

## Question description

<!--If you want to use the English description, use <p>You are given a binary string <code>binary</code>. A <strong>subsequence</strong> of <code>binary</code> is considered <strong>good</strong> if it is <strong>not empty</strong> and has <strong>no leading zeros</strong> (with the exception of <code>&quot;0&quot;</code>).</p>

<p>Find the number of <strong>unique good subsequences</strong> of <code>binary</code>.</p>

<ul>
	<li>For example, if <code>binary = &quot;001&quot;</code>, then all the <strong>good</strong> subsequences are <code>[&quot;0&quot;, &quot;0&quot;, &quot;1&quot;]</code>, so the <strong>unique</strong> good subsequences are <code>&quot;0&quot;</code> and <code>&quot;1&quot;</code>. Note that subsequences <code>&quot;00&quot;</code>, <code>&quot;01&quot;</code>, and <code>&quot;001&quot;</code> are not good because they have leading zeros.</li>
</ul>

<p>Return <em>the number of <strong>unique good subsequences</strong> of </em><code>binary</code>. Since the answer may be very large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>A <strong>subsequence</strong> is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> binary = &quot;001&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> The good subsequences of binary are [&quot;0&quot;, &quot;0&quot;, &quot;1&quot;].
The unique good subsequences are &quot;0&quot; and &quot;1&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> binary = &quot;11&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> The good subsequences of binary are [&quot;1&quot;, &quot;1&quot;, &quot;11&quot;].
The unique good subsequences are &quot;1&quot; and &quot;11&quot;.</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> binary = &quot;101&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The good subsequences of binary are [&quot;1&quot;, &quot;0&quot;, &quot;1&quot;, &quot;10&quot;, &quot;11&quot;, &quot;101&quot;]. 
The unique good subsequences are &quot;0&quot;, &quot;1&quot;, &quot;10&quot;, &quot;11&quot;, and &quot;101&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= binary.length &lt;= 10<sup>5</sup></code></li>
	<li><code>binary</code> consists of only <code>&#39;0&#39;</code>s and <code>&#39;1&#39;</code>s.</li>
</ul>
 instead-->
<p>给你一个二进制字符串&nbsp;<code>binary</code>&nbsp;。&nbsp;<code>binary</code>&nbsp;的一个 <strong>子序列</strong>&nbsp;如果是 <strong>非空</strong>&nbsp;的且没有 <b>前导</b>&nbsp;<strong>0</strong>&nbsp;（除非数字是 <code>"0"</code>&nbsp;本身），那么它就是一个 <strong>好</strong>&nbsp;的子序列。</p>

<p>请你找到&nbsp;<code>binary</code>&nbsp;<strong>不同好子序列</strong>&nbsp;的数目。</p>

<ul>
	<li>比方说，如果&nbsp;<code>binary = "001"</code>&nbsp;，那么所有 <strong>好</strong>&nbsp;子序列为&nbsp;<code>["0", "0", "1"]</code>&nbsp;，所以 <b>不同</b>&nbsp;的好子序列为&nbsp;<code>"0"</code> 和&nbsp;<code>"1"</code>&nbsp;。 注意，子序列&nbsp;<code>"00"</code>&nbsp;，<code>"01"</code>&nbsp;和&nbsp;<code>"001"</code>&nbsp;不是好的，因为它们有前导 0 。</li>
</ul>

<p>请你返回&nbsp;<code>binary</code>&nbsp;中&nbsp;<strong>不同好子序列</strong>&nbsp;的数目。由于答案可能很大，请将它对&nbsp;<code>10<sup>9</sup> + 7</code>&nbsp;<strong>取余</strong> 后返回。</p>

<p>一个 <strong>子序列</strong>&nbsp;指的是从原数组中删除若干个（可以一个也不删除）元素后，不改变剩余元素顺序得到的序列。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>binary = "001"
<b>输出：</b>2
<b>解释：</b>好的二进制子序列为 ["0", "0", "1"] 。
不同的好子序列为 "0" 和 "1" 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>binary = "11"
<b>输出：</b>2
<b>解释：</b>好的二进制子序列为 ["1", "1", "11"] 。
不同的好子序列为 "1" 和 "11" 。</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>binary = "101"
<b>输出：</b>5
<b>解释：</b>好的二进制子序列为 ["1", "0", "1", "10", "11", "101"] 。
不同的好子序列为 "0" ，"1" ，"10" ，"11" 和 "101" 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= binary.length &lt;= 10<sup>5</sup></code></li>
	<li><code>binary</code>&nbsp;只含有&nbsp;<code>'0'</code>&nbsp;和&nbsp;<code>'1'</code> 。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 18 ms

```java
class Solution {
    public int numberOfUniqueGoodSubsequences(String binary) {
        int mod = (int)1e9+7;
        long zero = 0, one = 0, ans = 0;
        boolean hasZero = false;// 以前是否出现过 0
        for (char ch : binary.toCharArray()) {
            if (ch=='0') {// 以 0 结尾的不同的好子序列数目
                zero = ans;
                if (!hasZero) {
                    ++zero;
                    hasZero = true;
                }
                zero %= mod;
            } else {// 以 1 结尾的不同的好子序列数目
                one = ans;
                if (!hasZero) ++one;
                one %= mod;
            }
            // 所有的不同的好子序列数目
            ans = one + zero;
            ans %= mod;
        }
        return (int)ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-unique-good-subsequences/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-unique-good-subsequences/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-unique-good-subsequences/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-unique-good-subsequences/)

[回到目录](../README.md)