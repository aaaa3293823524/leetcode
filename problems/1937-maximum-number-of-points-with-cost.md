# 1937. maximum-number-of-points-with-cost | 扣分后的最大得分

## Question description

<!--If you want to use the English description, use <p>You are given an <code>m x n</code> integer matrix <code>points</code> (<strong>0-indexed</strong>). Starting with <code>0</code> points, you want to <strong>maximize</strong> the number of points you can get from the matrix.</p>

<p>To gain points, you must pick one cell in <strong>each row</strong>. Picking the cell at coordinates <code>(r, c)</code> will <strong>add</strong> <code>points[r][c]</code> to your score.</p>

<p>However, you will lose points if you pick a cell too far from the cell that you picked in the previous row. For every two adjacent rows <code>r</code> and <code>r + 1</code> (where <code>0 &lt;= r &lt; m - 1</code>), picking cells at coordinates <code>(r, c<sub>1</sub>)</code> and <code>(r + 1, c<sub>2</sub>)</code> will <strong>subtract</strong> <code>abs(c<sub>1</sub> - c<sub>2</sub>)</code> from your score.</p>

<p>Return <em>the <strong>maximum</strong> number of points you can achieve</em>.</p>

<p><code>abs(x)</code> is defined as:</p>

<ul>
	<li><code>x</code> for <code>x &gt;= 0</code>.</li>
	<li><code>-x</code> for <code>x &lt; 0</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong><strong> </strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/12/screenshot-2021-07-12-at-13-40-26-diagram-drawio-diagrams-net.png" style="width: 300px; height: 300px;" />
<pre>
<strong>Input:</strong> points = [[1,2,3],[1,5,1],[3,1,1]]
<strong>Output:</strong> 9
<strong>Explanation:</strong>
The blue cells denote the optimal cells to pick, which have coordinates (0, 2), (1, 1), and (2, 0).
You add 3 + 5 + 3 = 11 to your score.
However, you must subtract abs(2 - 1) + abs(1 - 0) = 2 from your score.
Your final score is 11 - 2 = 9.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/12/screenshot-2021-07-12-at-13-42-14-diagram-drawio-diagrams-net.png" style="width: 200px; height: 299px;" />
<pre>
<strong>Input:</strong> points = [[1,5],[2,3],[4,2]]
<strong>Output:</strong> 11
<strong>Explanation:</strong>
The blue cells denote the optimal cells to pick, which have coordinates (0, 1), (1, 1), and (2, 0).
You add 5 + 3 + 4 = 12 to your score.
However, you must subtract abs(1 - 1) + abs(1 - 0) = 1 from your score.
Your final score is 12 - 1 = 11.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == points.length</code></li>
	<li><code>n == points[r].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= m * n &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= points[r][c] &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>给你一个 <code>m x n</code> 的整数矩阵 <code>points</code> （下标从 <strong>0</strong> 开始）。一开始你的得分为 <code>0</code> ，你想最大化从矩阵中得到的分数。</p>

<p>你的得分方式为：<strong>每一行</strong> 中选取一个格子，选中坐标为 <code>(r, c)</code> 的格子会给你的总得分 <strong>增加</strong> <code>points[r][c]</code> 。</p>

<p>然而，相邻行之间被选中的格子如果隔得太远，你会失去一些得分。对于相邻行 <code>r</code> 和 <code>r + 1</code> （其中 <code>0 <= r < m - 1</code>），选中坐标为 <code>(r, c<sub>1</sub>)</code> 和 <code>(r + 1, c<sub>2</sub>)</code> 的格子，你的总得分 <b>减少</b> <code>abs(c<sub>1</sub> - c<sub>2</sub>)</code> 。</p>

<p>请你返回你能得到的 <strong>最大</strong> 得分。</p>

<p><code>abs(x)</code> 定义为：</p>

<ul>
	<li>如果 <code>x >= 0</code> ，那么值为 <code>x</code> 。</li>
	<li>如果 <code>x < 0</code> ，那么值为 <code>-x</code> 。</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/12/screenshot-2021-07-12-at-13-40-26-diagram-drawio-diagrams-net.png" style="width: 300px; height: 300px;" />
<pre>
<b>输入：</b>points = [[1,2,3],[1,5,1],[3,1,1]]
<b>输出：</b>9
<strong>解释：</strong>
蓝色格子是最优方案选中的格子，坐标分别为 (0, 2)，(1, 1) 和 (2, 0) 。
你的总得分增加 3 + 5 + 3 = 11 。
但是你的总得分需要扣除 abs(2 - 1) + abs(1 - 0) = 2 。
你的最终得分为 11 - 2 = 9 。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/12/screenshot-2021-07-12-at-13-42-14-diagram-drawio-diagrams-net.png" style="width: 200px; height: 299px;" />
<pre>
<b>输入：</b>points = [[1,5],[2,3],[4,2]]
<b>输出：</b>11
<strong>解释：</strong>
蓝色格子是最优方案选中的格子，坐标分别为 (0, 1)，(1, 1) 和 (2, 0) 。
你的总得分增加 5 + 3 + 4 = 12 。
但是你的总得分需要扣除 abs(1 - 1) + abs(1 - 0) = 1 。
你的最终得分为 12 - 1 = 11 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == points.length</code></li>
	<li><code>n == points[r].length</code></li>
	<li><code>1 <= m, n <= 10<sup>5</sup></code></li>
	<li><code>1 <= m * n <= 10<sup>5</sup></code></li>
	<li><code>0 <= points[r][c] <= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 11 ms

```java
class Solution {
    //dp[i][j] =  points[i][j] + max{dp[i-1][k] - abs(j -k)}
    //dp[i][j]指取(i,j)下标的元素能达到的最大值
    //优化后变成
    //k<=j k在j左边 dp[i][j] =  points[i][j] - j + max{dp[i-1][k] + k}
    //k> j k在j右边 dp[i][j] =  points[i][j] + j + max{dp[i-1][k] - k}
    public long maxPoints(int[][] points) {
        int m = points.length;
        int n = points[0].length;
        long[] pre = new long[n];//记录上一行的值
        //由于某行的dp值只与上一行的值有关，故只需要两个long[n]的数组作为dp数组做状态转移。
        for (int[] point : points) {
            long[] cur = new long[n];//记录这一行的dp值
            long best = Long.MIN_VALUE;
            //正序遍历
            //为何要正序，因为这时是在k在j左边的情况，那么max{dp[i-1][k] + k}中的k可取[0,j]
            for (int j = 0; j < n; j++) {
                best = Math.max(best, pre[j] + j);//相当于max{dp[i-1][k] + k}的操作
                cur[j] = Math.max(cur[j], point[j] - j + best);
            }
            best = Long.MIN_VALUE;
            //倒序遍历
            //为何要倒序，因为这时是k在j右边的情况，那么max{dp[i-1][k] - k}中的k可取[j,n-1]
            for(int j = n-1;j>=0;j--){
                best = Math.max(best, pre[j] - j);//再倒序遍历，找上一行最大的dp[i-1][k]-k
                cur[j] = Math.max(cur[j], best + point[j] + j);
            }
            pre = cur;
        }
        return Arrays.stream(pre).max().getAsLong();//在最后一层找最大值
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-number-of-points-with-cost/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-number-of-points-with-cost/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-number-of-points-with-cost/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-number-of-points-with-cost/)

[回到目录](../README.md)