# 2008. maximum-earnings-from-taxi | 出租车的最大盈利

## Question description

<!--If you want to use the English description, use <p>There are <code>n</code> points on a road you are driving your taxi on. The <code>n</code> points on the road are labeled from <code>1</code> to <code>n</code> in the direction you are going, and you want to drive from point <code>1</code> to point <code>n</code> to make money by picking up passengers. You cannot change the direction of the taxi.</p>

<p>The passengers are represented by a <strong>0-indexed</strong> 2D integer array <code>rides</code>, where <code>rides[i] = [start<sub>i</sub>, end<sub>i</sub>, tip<sub>i</sub>]</code> denotes the <code>i<sup>th</sup></code> passenger requesting a ride from point <code>start<sub>i</sub></code> to point <code>end<sub>i</sub></code> who is willing to give a <code>tip<sub>i</sub></code> dollar tip.</p>

<p>For<strong> each </strong>passenger <code>i</code> you pick up, you <strong>earn</strong> <code>end<sub>i</sub> - start<sub>i</sub> + tip<sub>i</sub></code> dollars. You may only drive <b>at most one </b>passenger at a time.</p>

<p>Given <code>n</code> and <code>rides</code>, return <em>the <strong>maximum</strong> number of dollars you can earn by picking up the passengers optimally.</em></p>

<p><strong>Note:</strong> You may drop off a passenger and pick up a different passenger at the same point.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 5, rides = [<u>[2,5,4]</u>,[1,5,1]]
<strong>Output:</strong> 7
<strong>Explanation:</strong> We can pick up passenger 0 to earn 5 - 2 + 4 = 7 dollars.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 20, rides = [[1,6,1],<u>[3,10,2]</u>,<u>[10,12,3]</u>,[11,12,2],[12,15,2],<u>[13,18,1]</u>]
<strong>Output:</strong> 20
<strong>Explanation:</strong> We will pick up the following passengers:
- Drive passenger 1 from point 3 to point 10 for a profit of 10 - 3 + 2 = 9 dollars.
- Drive passenger 2 from point 10 to point 12 for a profit of 12 - 10 + 3 = 5 dollars.
- Drive passenger 5 from point 13 to point 18 for a profit of 18 - 13 + 1 = 6 dollars.
We earn 9 + 5 + 6 = 20 dollars in total.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= rides.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>rides[i].length == 3</code></li>
	<li><code>1 &lt;= start<sub>i</sub> &lt; end<sub>i</sub> &lt;= n</code></li>
	<li><code>1 &lt;= tip<sub>i</sub> &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>你驾驶出租车行驶在一条有 <code>n</code>&nbsp;个地点的路上。这 <code>n</code>&nbsp;个地点从近到远编号为&nbsp;<code>1</code>&nbsp;到&nbsp;<code>n</code>&nbsp;，你想要从 <code>1</code>&nbsp;开到 <code>n</code>&nbsp;，通过接乘客订单盈利。你只能沿着编号递增的方向前进，不能改变方向。</p>

<p>乘客信息用一个下标从 <strong>0</strong>&nbsp;开始的二维数组&nbsp;<code>rides</code>&nbsp;表示，其中&nbsp;<code>rides[i] = [start<sub>i</sub>, end<sub>i</sub>, tip<sub>i</sub>]</code>&nbsp;表示第&nbsp;<code>i</code>&nbsp;位乘客需要从地点&nbsp;<code>start<sub>i</sub></code>&nbsp;前往&nbsp;<code>end<sub>i</sub></code>&nbsp;，愿意支付&nbsp;<code>tip<sub>i</sub></code>&nbsp;元的小费。</p>

<p><strong>每一位</strong> 你选择接单的乘客&nbsp;<code>i</code>&nbsp;，你可以 <strong>盈利</strong>&nbsp;<code>end<sub>i</sub> - start<sub>i</sub> + tip<sub>i</sub></code>&nbsp;元。你同时&nbsp;<strong>最多</strong>&nbsp;只能接一个订单。</p>

<p>给你 <code>n</code>&nbsp;和 <code>rides</code>&nbsp;，请你返回在最优接单方案下，你能盈利&nbsp;<strong>最多</strong>&nbsp;多少元。</p>

<p><strong>注意：</strong>你可以在一个地点放下一位乘客，并在同一个地点接上另一位乘客。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>n = 5, rides = [<em><strong>[2,5,4]</strong></em>,[1,5,1]]
<b>输出：</b>7
<b>解释：</b>我们可以接乘客 0 的订单，获得 5 - 2 + 4 = 7 元。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>n = 20, rides = [[1,6,1],<strong><em>[3,10,2]</em></strong>,<em><strong>[10,12,3]</strong></em>,[11,12,2],[12,15,2],<strong><em>[13,18,1]</em></strong>]
<b>输出：</b>20
<b>解释：</b>我们可以接以下乘客的订单：
- 将乘客 1 从地点 3 送往地点 10 ，获得 10 - 3 + 2 = 9 元。
- 将乘客 2 从地点 10 送往地点 12 ，获得 12 - 10 + 3 = 5 元。
- 将乘客 5 从地点 13 送往地点 18 ，获得 18 - 13 + 1 = 6 元。
我们总共获得 9 + 5 + 6 = 20 元。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= rides.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>rides[i].length == 3</code></li>
	<li><code>1 &lt;= start<sub>i</sub> &lt; end<sub>i</sub> &lt;= n</code></li>
	<li><code>1 &lt;= tip<sub>i</sub> &lt;= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 58 ms

```java
class Solution {
    public long maxTaxiEarnings(int n, int[][] rides) {
        long[] dp = new long[n + 1];
        //按终点由小到大排序
        Arrays.sort(rides, (a, b) -> a[1] - b[1]);
        int index = 0;
        for (int i = 1; i <= n; i++) {
            //出租车从i-1位置走到i位置,不载人时他的最大收益等于dp[i-1]
            dp[i] = dp[i - 1];
            //int index = 0;
            while (index < rides.length && rides[index][1] <= i) {
                //更新以i为终点载人情况的最大盈利
                dp[i] = Math.max(dp[i], dp[rides[index][0]] + rides[index][1] - rides[index][0] + rides[index][2]);
                index++;
            }
        }
        return dp[n];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-earnings-from-taxi/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-earnings-from-taxi/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-earnings-from-taxi/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-earnings-from-taxi/)

[回到目录](../README.md)