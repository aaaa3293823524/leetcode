# 1553. minimum-number-of-days-to-eat-n-oranges | 吃掉 N 个橘子的最少天数

## Question description

<!--If you want to use the English description, use <p>There are <code>n</code> oranges in the kitchen and you decided to eat some of these oranges every day as follows:</p>

<ul>
	<li>Eat one orange.</li>
	<li>If the number of remaining oranges n&nbsp;is divisible by <code>2</code> then you can eat <code>n / 2</code> oranges.</li>
	<li>If the number of remaining oranges n&nbsp;is divisible by <code>3</code> then you can eat <code>2 * (n / 3)</code> oranges.</li>
</ul>

<p>You can only choose one of the actions per day.</p>

<p>Return the minimum number of days to eat <code>n</code> oranges.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> 4
<strong>Explanation:</strong> You have 10 oranges.
Day 1: Eat 1 orange,  10 - 1 = 9.  
Day 2: Eat 6 oranges, 9 - 2*(9/3) = 9 - 6 = 3. (Since 9 is divisible by 3)
Day 3: Eat 2 oranges, 3 - 2*(3/3) = 3 - 2 = 1. 
Day 4: Eat the last orange  1 - 1  = 0.
You need at least 4 days to eat the 10 oranges.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 6
<strong>Output:</strong> 3
<strong>Explanation:</strong> You have 6 oranges.
Day 1: Eat 3 oranges, 6 - 6/2 = 6 - 3 = 3. (Since 6 is divisible by 2).
Day 2: Eat 2 oranges, 3 - 2*(3/3) = 3 - 2 = 1. (Since 3 is divisible by 3)
Day 3: Eat the last orange  1 - 1  = 0.
You need at least 3 days to eat the 6 oranges.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> 1
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> n = 56
<strong>Output:</strong> 6
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2 * 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>厨房里总共有 <code>n</code>&nbsp;个橘子，你决定每一天选择如下方式之一吃这些橘子：</p>

<ul>
	<li>吃掉一个橘子。</li>
	<li>如果剩余橘子数 <code>n</code>&nbsp;能被 2 整除，那么你可以吃掉 <code>n/2</code> 个橘子。</li>
	<li>如果剩余橘子数&nbsp;<code>n</code>&nbsp;能被 3 整除，那么你可以吃掉 <code>2*(n/3)</code> 个橘子。</li>
</ul>

<p>每天你只能从以上 3 种方案中选择一种方案。</p>

<p>请你返回吃掉所有 <code>n</code>&nbsp;个橘子的最少天数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>n = 10
<strong>输出：</strong>4
<strong>解释：</strong>你总共有 10 个橘子。
第 1 天：吃 1 个橘子，剩余橘子数 10 - 1 = 9。
第 2 天：吃 6 个橘子，剩余橘子数 9 - 2*(9/3) = 9 - 6 = 3。（9 可以被 3 整除）
第 3 天：吃 2 个橘子，剩余橘子数 3 - 2*(3/3) = 3 - 2 = 1。
第 4 天：吃掉最后 1 个橘子，剩余橘子数 1 - 1 = 0。
你需要至少 4 天吃掉 10 个橘子。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>n = 6
<strong>输出：</strong>3
<strong>解释：</strong>你总共有 6 个橘子。
第 1 天：吃 3 个橘子，剩余橘子数 6 - 6/2 = 6 - 3 = 3。（6 可以被 2 整除）
第 2 天：吃 2 个橘子，剩余橘子数 3 - 2*(3/3) = 3 - 2 = 1。（3 可以被 3 整除）
第 3 天：吃掉剩余 1 个橘子，剩余橘子数 1 - 1 = 0。
你至少需要 3 天吃掉 6 个橘子。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>n = 1
<strong>输出：</strong>1
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>n = 56
<strong>输出：</strong>6
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2*10^9</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    Map<Integer, Integer> memo = new HashMap<Integer, Integer>();

    public int minDays(int n) {
        if (n <= 1) {
            return n;
        }
        if (memo.containsKey(n)) {
            return memo.get(n);
        }
        memo.put(n, Math.min(n % 2 + 1 + minDays(n / 2), n % 3 + 1 + minDays(n / 3)));
        return memo.get(n);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-number-of-days-to-eat-n-oranges/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-number-of-days-to-eat-n-oranges/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-number-of-days-to-eat-n-oranges/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-number-of-days-to-eat-n-oranges/)

[回到目录](../README.md)