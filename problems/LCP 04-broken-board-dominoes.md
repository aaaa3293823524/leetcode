# LCP 04. broken-board-dominoes | 覆盖

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>你有一块棋盘，棋盘上有一些格子已经坏掉了。你还有无穷块大小为<code>1 * 2</code>的多米诺骨牌，你想把这些骨牌<strong>不重叠</strong>地覆盖在<strong>完好</strong>的格子上，请找出你最多能在棋盘上放多少块骨牌？这些骨牌可以横着或者竖着放。</p>

<p>&nbsp;</p>

<p>输入：<code>n, m</code>代表棋盘的大小；<code>broken</code>是一个<code>b * 2</code>的二维数组，其中每个元素代表棋盘上每一个坏掉的格子的位置。</p>

<p>输出：一个整数，代表最多能在棋盘上放的骨牌数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>n = 2, m = 3, broken = [[1, 0], [1, 1]]
<strong>输出：</strong>2
<strong>解释：</strong>我们最多可以放两块骨牌：[[0, 0], [0, 1]]以及[[0, 2], [1, 2]]。（见下图）</pre>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/09/09/domino_example_1.jpg" style="height: 204px; width: 304px;"></p>

<p>&nbsp;</p>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>n = 3, m = 3, broken = []
<strong>输出：</strong>4
<strong>解释：</strong>下图是其中一种可行的摆放方式
</pre>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/09/09/domino_example_2.jpg" style="height: 304px; width: 304px;"></p>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ol>
	<li><code>1 &lt;= n &lt;= 8</code></li>
	<li><code>1 &lt;= m &lt;= 8</code></li>
	<li><code>0 &lt;= b &lt;= n * m</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 9 ms

```java
class Solution {
    int [][]dp;
    boolean [][]vis;
    void dfs(int sta, int cur, int row, int col, int m, int now) {
        if (col == m) {dp[row][cur] = Math.max(dp[row][cur], now + dp[row - 1][sta]);return;}
        if (vis[row][col]) {
            dfs(sta, cur | (1 << col), row, col + 1, m, now);
        } else {
            if (col + 2 <= m && vis[row][col + 1] == false) {
                int tmp = cur | (1 << col);
                tmp = tmp | (1 << (col + 1));
                dfs(sta, tmp, row, col + 2, m, now + 1);
            }
            if (((sta >> col) & 1) != 1) {
                dfs(sta, cur | (1 << col), row, col + 1, m, now + 1);
            } else {
                dfs(sta, cur, row, col + 1, m, now);
            }
        }
    }
    public int domino(int n, int m, int[][] broken) {
        dp = new int[n + 1][(1 << m)];
        vis = new boolean[n + 1][m];
        for (int[]tmp : broken) {vis[tmp[0] + 1][tmp[1]] = true;};
        for (int i = 0; i <= n; ++i) Arrays.fill(dp[i], -99999);
        dp[0][(1 << m) - 1] = 0;
        for (int i = 1; i <= n; ++i) {
            for (int sta = 0; sta < (1 << m); ++sta) {
                dfs(sta, 0, i, 0, m, 0);
            }
        }
        int ans = -99999;
        for (int i = 0; i < (1 << m); ++i) ans = Math.max(dp[n][i], ans);
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/broken-board-dominoes/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/broken-board-dominoes/description/)

Solution: [LeetCode](https://leetcode.com/articles/broken-board-dominoes/)  /  [LeetCode中国](https://leetcode-cn.com/articles/broken-board-dominoes/)

[回到目录](../README.md)