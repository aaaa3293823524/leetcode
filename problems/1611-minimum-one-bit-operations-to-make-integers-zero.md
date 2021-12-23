# 1611. minimum-one-bit-operations-to-make-integers-zero | 使整数变为 0 的最少操作次数

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>n</code>, you must transform it into <code>0</code> using the following operations any number of times:</p>

<ul>
	<li>Change the rightmost (<code>0<sup>th</sup></code>) bit in the binary representation of <code>n</code>.</li>
	<li>Change the <code>i<sup>th</sup></code> bit in the binary representation of <code>n</code> if the <code>(i-1)<sup>th</sup></code> bit is set to <code>1</code> and the <code>(i-2)<sup>th</sup></code> through <code>0<sup>th</sup></code> bits are set to <code>0</code>.</li>
</ul>

<p>Return <em>the minimum number of operations to transform </em><code>n</code><em> into </em><code>0</code><em>.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 3
<strong>Output:</strong> 2
<strong>Explanation:</strong> The binary representation of 3 is &quot;11&quot;.
&quot;<u>1</u>1&quot; -&gt; &quot;<u>0</u>1&quot; with the 2<sup>nd</sup> operation since the 0<sup>th</sup> bit is 1.
&quot;0<u>1</u>&quot; -&gt; &quot;0<u>0</u>&quot; with the 1<sup>st</sup> operation.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 6
<strong>Output:</strong> 4
<strong>Explanation:</strong> The binary representation of 6 is &quot;110&quot;.
&quot;<u>1</u>10&quot; -&gt; &quot;<u>0</u>10&quot; with the 2<sup>nd</sup> operation since the 1<sup>st</sup> bit is 1 and 0<sup>th</sup> through 0<sup>th</sup> bits are 0.
&quot;01<u>0</u>&quot; -&gt; &quot;01<u>1</u>&quot; with the 1<sup>st</sup> operation.
&quot;0<u>1</u>1&quot; -&gt; &quot;0<u>0</u>1&quot; with the 2<sup>nd</sup> operation since the 0<sup>th</sup> bit is 1.
&quot;00<u>1</u>&quot; -&gt; &quot;00<u>0</u>&quot; with the 1<sup>st</sup> operation.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给你一个整数 <code>n</code>，你需要重复执行多次下述操作将其转换为 <code>0</code> ：</p>

<ul>
	<li>翻转 <code>n</code> 的二进制表示中最右侧位（第 <code>0</code> 位）。</li>
	<li>如果第 <code>(i-1)</code> 位为 <code>1</code> 且从第 <code>(i-2)</code> 位到第 <code>0</code> 位都为 <code>0</code>，则翻转 <code>n</code> 的二进制表示中的第 <code>i</code> 位。</li>
</ul>

<p>返回将 <code>n</code> 转换为 <code>0</code> 的最小操作次数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 0
<strong>输出：</strong>0
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 3
<strong>输出：</strong>2
<strong>解释：</strong>3 的二进制表示为 "11"
"<strong>1</strong>1" -> "<strong>0</strong>1" ，执行的是第 2 种操作，因为第 0 位为 1 。
"0<strong>1</strong>" -> "0<strong>0</strong>" ，执行的是第 1 种操作。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>n = 6
<strong>输出：</strong>4
<strong>解释：</strong>6 的二进制表示为 "110".
"<strong>1</strong>10" -> "<strong>0</strong>10" ，执行的是第 2 种操作，因为第 1 位为 1 ，第 0 到 0 位为 0 。
"01<strong>0</strong>" -> "01<strong>1</strong>" ，执行的是第 1 种操作。
"0<strong>1</strong>1" -> "0<strong>0</strong>1" ，执行的是第 2 种操作，因为第 0 位为 1 。
"00<strong>1</strong>" -> "00<strong>0</strong>" ，执行的是第 1 种操作。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>n = 9
<strong>输出：</strong>14
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>n = 333
<strong>输出：</strong>393
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= n <= 10<sup>9</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int minimumOneBitOperations(int n){
        if(n==0) return 0;
        if(n==1) return 1;
        int t=2;
        while(t<=n)  t*=2;
        return t-1-minimumOneBitOperations(n-t/2);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-one-bit-operations-to-make-integers-zero/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-one-bit-operations-to-make-integers-zero/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-one-bit-operations-to-make-integers-zero/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-one-bit-operations-to-make-integers-zero/)

[回到目录](../README.md)