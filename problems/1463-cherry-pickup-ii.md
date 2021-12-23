# 1463. cherry-pickup-ii | 摘樱桃 II

## Question description

<!--If you want to use the English description, use <p>Given a <code>rows x cols</code> matrix <code>grid</code> representing a field of cherries.&nbsp;Each cell in&nbsp;<code>grid</code>&nbsp;represents the number of cherries that you can collect.</p>

<p>You have two&nbsp;robots that can collect cherries for you, Robot #1 is located at the top-left corner (0,0) , and Robot #2 is located at the top-right corner (0, cols-1) of the grid.</p>

<p>Return the maximum number of cherries collection using both robots&nbsp; by following the rules below:</p>

<ul>
	<li>From a cell (i,j), robots can move to cell (i+1, j-1) , (i+1, j) or (i+1, j+1).</li>
	<li>When any robot is passing through a cell, It picks it up all cherries, and the cell becomes an empty cell (0).</li>
	<li>When both robots stay on the same cell, only one of them takes the cherries.</li>
	<li>Both robots cannot move outside of the grid at&nbsp;any moment.</li>
	<li>Both robots should reach the bottom row in the <code>grid</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2020/04/29/sample_1_1802.png" style="width: 139px; height: 182px;" /></strong></p>

<pre>
<strong>Input:</strong> grid = [[3,1,1],[2,5,1],[1,5,5],[2,1,1]]
<strong>Output:</strong> 24
<strong>Explanation:</strong>&nbsp;Path of robot #1 and #2 are described in color green and blue respectively.
Cherries taken by Robot #1, (3 + 2 + 5 + 2) = 12.
Cherries taken by Robot #2, (1 + 5 + 5 + 1) = 12.
Total of cherries: 12 + 12 = 24.
</pre>

<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2020/04/23/sample_2_1802.png" style="width: 284px; height: 257px;" /></strong></p>

<pre>
<strong>Input:</strong> grid = [[1,0,0,0,0,0,1],[2,0,0,0,0,3,0],[2,0,9,0,0,0,0],[0,3,0,5,4,0,0],[1,0,2,3,0,0,6]]
<strong>Output:</strong> 28
<strong>Explanation:</strong>&nbsp;Path of robot #1 and #2 are described in color green and blue respectively.
Cherries taken by Robot #1, (1 + 9 + 5 + 2) = 17.
Cherries taken by Robot #2, (1 + 3 + 4 + 3) = 11.
Total of cherries: 17 + 11 = 28.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1,0,0,3],[0,0,0,3],[0,0,3,3],[9,0,3,3]]
<strong>Output:</strong> 22
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1,1],[1,1]]
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>rows == grid.length</code></li>
	<li><code>cols == grid[i].length</code></li>
	<li><code>2 &lt;= rows, cols &lt;= 70</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 100&nbsp;</code></li>
</ul>
 instead-->
<p>给你一个&nbsp;<code>rows x cols</code> 的矩阵&nbsp;<code>grid</code>&nbsp;来表示一块樱桃地。 <code>grid</code>&nbsp;中每个格子的数字表示你能获得的樱桃数目。</p>

<p>你有两个机器人帮你收集樱桃，机器人 1 从左上角格子 <code>(0,0)</code> 出发，机器人 2 从右上角格子 <code>(0, cols-1)</code> 出发。</p>

<p>请你按照如下规则，返回两个机器人能收集的最多樱桃数目：</p>

<ul>
	<li>从格子&nbsp;<code>(i,j)</code> 出发，机器人可以移动到格子&nbsp;<code>(i+1, j-1)</code>，<code>(i+1, j)</code> 或者&nbsp;<code>(i+1, j+1)</code>&nbsp;。</li>
	<li>当一个机器人经过某个格子时，它会把该格子内所有的樱桃都摘走，然后这个位置会变成空格子，即没有樱桃的格子。</li>
	<li>当两个机器人同时到达同一个格子时，它们中只有一个可以摘到樱桃。</li>
	<li>两个机器人在任意时刻都不能移动到 <code>grid</code>&nbsp;外面。</li>
	<li>两个机器人最后都要到达&nbsp;<code>grid</code>&nbsp;最底下一行。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/05/30/sample_1_1802.png" style="height: 182px; width: 139px;"></strong></p>

<pre><strong>输入：</strong>grid = [[3,1,1],[2,5,1],[1,5,5],[2,1,1]]
<strong>输出：</strong>24
<strong>解释：</strong>机器人 1 和机器人 2 的路径在上图中分别用绿色和蓝色表示。
机器人 1 摘的樱桃数目为 (3 + 2 + 5 + 2) = 12 。
机器人 2 摘的樱桃数目为 (1 + 5 + 5 + 1) = 12 。
樱桃总数为： 12 + 12 = 24 。
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/05/30/sample_2_1802.png" style="height: 257px; width: 284px;"></strong></p>

<pre><strong>输入：</strong>grid = [[1,0,0,0,0,0,1],[2,0,0,0,0,3,0],[2,0,9,0,0,0,0],[0,3,0,5,4,0,0],[1,0,2,3,0,0,6]]
<strong>输出：</strong>28
<strong>解释：</strong>机器人 1 和机器人 2 的路径在上图中分别用绿色和蓝色表示。
机器人 1 摘的樱桃数目为 (1 + 9 + 5 + 2) = 17 。
机器人 2 摘的樱桃数目为 (1 + 3 + 4 + 3) = 11 。
樱桃总数为： 17 + 11 = 28 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>grid = [[1,0,0,3],[0,0,0,3],[0,0,3,3],[9,0,3,3]]
<strong>输出：</strong>22
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>grid = [[1,1],[1,1]]
<strong>输出：</strong>4
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>rows == grid.length</code></li>
	<li><code>cols == grid[i].length</code></li>
	<li><code>2 &lt;= rows, cols &lt;= 70</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 100&nbsp;</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 24 ms

```java
class Solution {
    public int cherryPickup(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        
        int[][] f = new int[n][n];
        int[][] g = new int[n][n];
        for (int i = 0; i < n; i++) {
            Arrays.fill(f[i], -1);
            Arrays.fill(g[i], -1);
        }
        f[0][n - 1] = grid[0][0] + grid[0][n - 1];
        for (int i = 1; i < m; ++i) {
            for (int j1 = 0; j1 < n; ++j1) {
                for (int j2 = 0; j2 < n; ++j2) {
                    int best = -1;
                    for (int dj1 = j1 - 1; dj1 <= j1 + 1; ++dj1) {
                        for (int dj2 = j2 - 1; dj2 <= j2 + 1; ++dj2) {
                            if (dj1 >= 0 && dj1 < n && dj2 >= 0 && dj2 < n && f[dj1][dj2] != -1) {
                                best = Math.max(best, f[dj1][dj2] + (j1 == j2 ? grid[i][j1] : grid[i][j1] + grid[i][j2]));
                            }
                        }
                    }
                    g[j1][j2] = best;
                }
            }
            int[][] temp = f;  //为什么交换？
            f = g;
            g = temp;
        }

        int ans = 0;
        for (int j1 = 0; j1 < n; ++j1) {
            for (int j2 = 0; j2 < n; ++j2) {
                ans = Math.max(ans, f[j1][j2]);
            }
        }
        return ans;

    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/cherry-pickup-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/cherry-pickup-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/cherry-pickup-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/cherry-pickup-ii/)

[回到目录](../README.md)