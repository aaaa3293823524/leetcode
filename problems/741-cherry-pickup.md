# 741. cherry-pickup | 摘樱桃

## Question description

<!--If you want to use the English description, use <p>You are given an <code>n x n</code> <code>grid</code> representing a field of cherries, each cell is one of three possible integers.</p>

<ul>
	<li><code>0</code> means the cell is empty, so you can pass through,</li>
	<li><code>1</code> means the cell contains a cherry that you can pick up and pass through, or</li>
	<li><code>-1</code> means the cell contains a thorn that blocks your way.</li>
</ul>

<p>Return <em>the maximum number of cherries you can collect by following the rules below</em>:</p>

<ul>
	<li>Starting at the position <code>(0, 0)</code> and reaching <code>(n - 1, n - 1)</code> by moving right or down through valid path cells (cells with value <code>0</code> or <code>1</code>).</li>
	<li>After reaching <code>(n - 1, n - 1)</code>, returning to <code>(0, 0)</code> by moving left or up through valid path cells.</li>
	<li>When passing through a path cell containing a cherry, you pick it up, and the cell becomes an empty cell <code>0</code>.</li>
	<li>If there is no valid path between <code>(0, 0)</code> and <code>(n - 1, n - 1)</code>, then no cherries can be collected.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/12/14/grid.jpg" style="width: 242px; height: 242px;" />
<pre>
<strong>Input:</strong> grid = [[0,1,-1],[1,0,-1],[1,1,1]]
<strong>Output:</strong> 5
<strong>Explanation:</strong> The player started at (0, 0) and went down, down, right right to reach (2, 2).
4 cherries were picked up during this single trip, and the matrix becomes [[0,1,-1],[0,0,-1],[0,0,0]].
Then, the player went left, up, up, left to return home, picking up one more cherry.
The total number of cherries picked up is 5, and this is the maximum possible.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1,1,-1],[1,-1,1],[-1,1,1]]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 50</code></li>
	<li><code>grid[i][j]</code> is <code>-1</code>, <code>0</code>, or <code>1</code>.</li>
	<li><code>grid[0][0] != -1</code></li>
	<li><code>grid[n - 1][n - 1] != -1</code></li>
</ul>
 instead-->
<p>一个N x N的网格<code>(grid)</code>&nbsp;代表了一块樱桃地，每个格子由以下三种数字的一种来表示：</p>

<ul>
	<li>0 表示这个格子是空的，所以你可以穿过它。</li>
	<li>1 表示这个格子里装着一个樱桃，你可以摘到樱桃然后穿过它。</li>
	<li>-1 表示这个格子里有荆棘，挡着你的路。</li>
</ul>

<p>你的任务是在遵守下列规则的情况下，尽可能的摘到最多樱桃：</p>

<ul>
	<li>从位置&nbsp;(0, 0) 出发，最后到达 (N-1, N-1) ，只能向下或向右走，并且只能穿越有效的格子（即只可以穿过值为0或者1的格子）；</li>
	<li>当到达 (N-1, N-1) 后，你要继续走，直到返回到 (0, 0) ，只能向上或向左走，并且只能穿越有效的格子；</li>
	<li>当你经过一个格子且这个格子包含一个樱桃时，你将摘到樱桃并且这个格子会变成空的（值变为0）；</li>
	<li>如果在 (0, 0) 和 (N-1, N-1) 之间不存在一条可经过的路径，则没有任何一个樱桃能被摘到。</li>
</ul>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> grid =
[[0, 1, -1],
 [1, 0, -1],
 [1, 1,  1]]
<strong>输出:</strong> 5
<strong>解释：</strong> 
玩家从（0,0）点出发，经过了向下走，向下走，向右走，向右走，到达了点(2, 2)。
在这趟单程中，总共摘到了4颗樱桃，矩阵变成了[[0,1,-1],[0,0,-1],[0,0,0]]。
接着，这名玩家向左走，向上走，向上走，向左走，返回了起始点，又摘到了1颗樱桃。
在旅程中，总共摘到了5颗樱桃，这是可以摘到的最大值了。
</pre>

<p><strong>说明:</strong></p>

<ul>
	<li><code>grid</code> 是一个&nbsp;<code>N</code> * <code>N</code> 的二维数组，N的取值范围是<code>1 &lt;= N &lt;= 50</code>。</li>
	<li>每一个&nbsp;<code>grid[i][j]</code> 都是集合&nbsp;<code>{-1, 0, 1}</code>其中的一个数。</li>
	<li>可以保证起点&nbsp;<code>grid[0][0]</code>&nbsp;和终点&nbsp;<code>grid[N-1][N-1]</code>&nbsp;的值都不会是 -1。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 16 ms

```java
class Solution {
    public int cherryPickup(int[][] grid) {
        int N = grid.length;
        int[][] dp = new int[N][N];
        for (int[] row : dp) {
            Arrays.fill(row, Integer.MIN_VALUE);
        }
        dp[0][0] = grid[0][0];

        // 一共要走 2 * N - 2 步，满足横纵坐标之和为 t
        for (int t = 1; t <= 2 * N - 2; t++) {
            int[][] dp2 = new int[N][N];
            for (int[] row : dp2) {
                Arrays.fill(row, Integer.MIN_VALUE);
            }

            // 枚举横坐标
            for (int i = Math.max(0, t - (N - 1)); i <= Math.min(N - 1, t); i++) {
                // 枚举纵坐标
                for (int j = Math.max(0, t - (N - 1)); j <= Math.min(N - 1, t); j++) {
                    // 遇到墙
                    if (grid[i][t - i] == -1 || grid[j][t - j] == -1) {
                        continue;
                    }

                    // 否则加上 0 或者加上 1
                    int res = grid[i][t - i];
                    if (i != j) {
                        // 不重合的时候加上另一个坐标
                        res += grid[j][t - j];
                    }

                    // 枚举上一步的坐标
                    for (int pi = i - 1; pi <= i; pi++) {
                        for (int pj = j - 1; pj <= j; pj++) {
                            if (pi >= 0 && pj >= 0) {
                                dp2[i][j] = Math.max(dp2[i][j], dp[pi][pj] + res);
                            }
                        }
                    }
                }
            }
            dp = dp2;
        }
        return Math.max(0, dp[N - 1][N - 1]);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/cherry-pickup/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/cherry-pickup/description/)

Solution: [LeetCode](https://leetcode.com/articles/cherry-pickup/)  /  [LeetCode中国](https://leetcode-cn.com/articles/cherry-pickup/)

[回到目录](../README.md)