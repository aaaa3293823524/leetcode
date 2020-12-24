# 309. best-time-to-buy-and-sell-stock-with-cooldown | 最佳买卖股票时机含冷冻期

## Question description

<!--If you want to use the English description, use <p>Say you have an array for which the <i>i</i><sup>th</sup> element is the price of a given stock on day <i>i</i>.</p>

<p>Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times) with the following restrictions:</p>

<ul>
	<li>You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).</li>
	<li>After you sell your stock, you cannot buy stock on next day. (ie, cooldown 1 day)</li>
</ul>

<p><b>Example:</b></p>

<pre>
<strong>Input:</strong> [1,2,3,0,2]
<strong>Output: </strong>3 
<strong>Explanation:</strong> transactions = [buy, sell, cooldown, buy, sell]
</pre> instead-->
<p>给定一个整数数组，其中第<em>&nbsp;i</em>&nbsp;个元素代表了第&nbsp;<em>i</em>&nbsp;天的股票价格 。​</p>

<p>设计一个算法计算出最大利润。在满足以下约束条件下，你可以尽可能地完成更多的交易（多次买卖一支股票）:</p>

<ul>
	<li>你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。</li>
	<li>卖出股票后，你无法在第二天买入股票 (即冷冻期为 1 天)。</li>
</ul>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> [1,2,3,0,2]
<strong>输出: </strong>3 
<strong>解释:</strong> 对应的交易状态为: [买入, 卖出, 冷冻期, 买入, 卖出]</pre>


## Note

对于力扣平台上的股票类型的题目：



121. 买卖股票的最佳时机



122. 买卖股票的最佳时机 II



123. 买卖股票的最佳时机 III



188. 买卖股票的最佳时机 IV



（本题）309. 最佳买卖股票时机含冷冻期



714. 买卖股票的最佳时机含手续费



剑指 Offer 63. 股票的最大利润



动态规划






## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public int maxProfit(int[] prices) {
        if (prices.length == 0) {
            return 0;
        }

        int n = prices.length;
        // f[i][0]: 手上持有股票的最大收益
        // f[i][1]: 手上不持有股票，并且处于冷冻期中的累计最大收益
        // f[i][2]: 手上不持有股票，并且不在冷冻期中的累计最大收益
        int[][] f = new int[n][3];
        f[0][0] = -prices[0];
        for (int i = 1; i < n; ++i) {
            f[i][0] = Math.max(f[i - 1][0], f[i - 1][2] - prices[i]);
            f[i][1] = f[i - 1][0] + prices[i];
            f[i][2] = Math.max(f[i - 1][1], f[i - 1][2]);
        }
        return Math.max(f[n - 1][1], f[n - 1][2]);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)

Solution: [LeetCode](https://leetcode.com/articles/best-time-to-buy-and-sell-stock-with-cooldown/)  /  [LeetCode中国](https://leetcode-cn.com/articles/best-time-to-buy-and-sell-stock-with-cooldown/)

[回到目录](../README.md)