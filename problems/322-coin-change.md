# 322. coin-change | 零钱兑换

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>coins</code> representing coins of different denominations and an integer <code>amount</code> representing a total amount of money.</p>

<p>Return <em>the fewest number of coins that you need to make up that amount</em>. If that amount of money cannot be made up by any combination of the coins, return <code>-1</code>.</p>

<p>You may assume that you have an infinite number of each kind of coin.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> coins = [1,2,5], amount = 11
<strong>Output:</strong> 3
<strong>Explanation:</strong> 11 = 5 + 5 + 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> coins = [2], amount = 3
<strong>Output:</strong> -1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> coins = [1], amount = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= coins.length &lt;= 12</code></li>
	<li><code>1 &lt;= coins[i] &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>0 &lt;= amount &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>coins</code> ，表示不同面额的硬币；以及一个整数 <code>amount</code> ，表示总金额。</p>

<p>计算并返回可以凑成总金额所需的 <strong>最少的硬币个数</strong> 。如果没有任何一种硬币组合能组成总金额，返回 <code>-1</code> 。</p>

<p>你可以认为每种硬币的数量是无限的。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>coins = <code>[1, 2, 5]</code>, amount = <code>11</code>
<strong>输出：</strong><code>3</code> 
<strong>解释：</strong>11 = 5 + 5 + 1</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>coins = <code>[2]</code>, amount = <code>3</code>
<strong>输出：</strong>-1</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>coins = [1], amount = 0
<strong>输出：</strong>0
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>coins = [1], amount = 1
<strong>输出：</strong>1
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>coins = [1], amount = 2
<strong>输出：</strong>2
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= coins.length <= 12</code></li>
	<li><code>1 <= coins[i] <= 2<sup>31</sup> - 1</code></li>
	<li><code>0 <= amount <= 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 12 ms

```java
public class Solution {
    public int coinChange(int[] coins, int amount) {
        int[]dp=new int[amount+1];
        
        Arrays.fill(dp, amount+1);
        dp[0]=0;
        for(int i=1;i<=amount;i++) {
            for(int j=0;j<coins.length;j++) {
                if(i>=coins[j])dp[i]=Math.min(dp[i],dp[i-coins[j]]+1);
            }
        }
        return dp[amount]>amount?-1:dp[amount];
    }
    // public int coinChange(int[] coins, int amount) {
    //     int max = amount + 1;
    //     int[] dp = new int[amount + 1];
    //     Arrays.fill(dp, max);
    //     dp[0] = 0;
    //     for (int i = 1; i <= amount; i++) {
    //         for (int j = 0; j < coins.length; j++) {
    //             if (coins[j] <= i) {
    //                 dp[i] = Math.min(dp[i], dp[i - coins[j]] + 1);
    //             }
    //         }
    //     }
    //     return dp[amount] > amount ? -1 : dp[amount];
    // }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/coin-change/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/coin-change/description/)

Solution: [LeetCode](https://leetcode.com/articles/coin-change/)  /  [LeetCode中国](https://leetcode-cn.com/articles/coin-change/)

[回到目录](../README.md)