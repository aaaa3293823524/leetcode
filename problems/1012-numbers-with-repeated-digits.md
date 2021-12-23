# 1012. numbers-with-repeated-digits | 至少有 1 位重复的数字

## Question description

<!--If you want to use the English description, use <p>Given an integer <code>n</code>, return <em>the number of positive integers in the range </em><code>[1, n]</code><em> that have <strong>at least one</strong> repeated digit</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 20
<strong>Output:</strong> 1
<strong>Explanation:</strong> The only positive number (&lt;= 20) with at least 1 repeated digit is 11.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 100
<strong>Output:</strong> 10
<strong>Explanation:</strong> The positive numbers (&lt;= 100) with atleast 1 repeated digit are 11, 22, 33, 44, 55, 66, 77, 88, 99, and 100.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 1000
<strong>Output:</strong> 262
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给定正整数&nbsp;<code>N</code>，返回小于等于 <code>N</code>&nbsp;且具有至少 1 位重复数字的正整数的个数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>20
<strong>输出：</strong>1
<strong>解释：</strong>具有至少 1 位重复数字的正数（&lt;= 20）只有 11 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>100
<strong>输出：</strong>10
<strong>解释：</strong>具有至少 1 位重复数字的正数（&lt;= 100）有 11，22，33，44，55，66，77，88，99 和 100 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>1000
<strong>输出：</strong>262
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= N &lt;= 10^9</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 12 ms

```java
class Solution {
    // 数位DP + 压缩状态 经典
    private int[][] dp;
    private int[] nums;
    public int numDupDigitsAtMostN(int N) {
        if (N <= 10) return 0;

        int temp = N + 1;

        // N 转化为数组
        nums = new int[10];
        int pos = 0;
        while (N != 0) {
            nums[pos++] = N % 10;
            N /= 10;
        }

        // 入记忆化深搜
        dp = new int[1 << 10][pos];
        for (int i = 0; i < (1 << 10); i++) {
            Arrays.fill(dp[i], -1);
        }

        // return dfs(pos - 1, 0, 1);
        return temp - dfs(pos - 1, 0, 1);
    }

    public int dfs(int pos, int mask, int limit) {
        // 递归返回条件0
        if (pos == -1) return 1;

        // 加入记忆化 (优化)
        if (dp[mask][pos] != -1 && limit == 0) return dp[mask][pos];

        int up = limit == 1 ? nums[pos] : 9;

        int res = 0;
        for (int i = 0; i <= up; i++) {
            // 首先当前位的状态没有出现过 
            //（本体计算的是不满足 至少两次的所有情况 逆向思维） 
            if ((mask & (1 << i)) == 0) {
                // 关键是理解下面 if - else
                if (i == 0 && mask == 0) { // 001的情况
                    res += dfs(pos - 1, mask, 0);
                } else {
                    res += dfs(pos - 1, mask | (1 << i), (limit == 1 && i == nums[pos]) ? 1 : 0);
                }
            }
        }

        if (limit == 0) dp[mask][pos] = res;

        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/numbers-with-repeated-digits/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/numbers-with-repeated-digits/description/)

Solution: [LeetCode](https://leetcode.com/articles/numbers-with-repeated-digits/)  /  [LeetCode中国](https://leetcode-cn.com/articles/numbers-with-repeated-digits/)

[回到目录](../README.md)