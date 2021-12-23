# 1905. count-sub-islands | 统计子岛屿

## Question description

<!--If you want to use the English description, use <p>You are given two <code>m x n</code> binary matrices <code>grid1</code> and <code>grid2</code> containing only <code>0</code>&#39;s (representing water) and <code>1</code>&#39;s (representing land). An <strong>island</strong> is a group of <code>1</code>&#39;s connected <strong>4-directionally</strong> (horizontal or vertical). Any cells outside of the grid are considered water cells.</p>

<p>An island in <code>grid2</code> is considered a <strong>sub-island </strong>if there is an island in <code>grid1</code> that contains <strong>all</strong> the cells that make up <strong>this</strong> island in <code>grid2</code>.</p>

<p>Return the <em><strong>number</strong> of islands in </em><code>grid2</code> <em>that are considered <strong>sub-islands</strong></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/10/test1.png" style="width: 493px; height: 205px;" />
<pre>
<strong>Input:</strong> grid1 = [[1,1,1,0,0],[0,1,1,1,1],[0,0,0,0,0],[1,0,0,0,0],[1,1,0,1,1]], grid2 = [[1,1,1,0,0],[0,0,1,1,1],[0,1,0,0,0],[1,0,1,1,0],[0,1,0,1,0]]
<strong>Output:</strong> 3
<strong>Explanation: </strong>In the picture above, the grid on the left is grid1 and the grid on the right is grid2.
The 1s colored red in grid2 are those considered to be part of a sub-island. There are three sub-islands.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/03/testcasex2.png" style="width: 491px; height: 201px;" />
<pre>
<strong>Input:</strong> grid1 = [[1,0,1,0,1],[1,1,1,1,1],[0,0,0,0,0],[1,1,1,1,1],[1,0,1,0,1]], grid2 = [[0,0,0,0,0],[1,1,1,1,1],[0,1,0,1,0],[0,1,0,1,0],[1,0,0,0,1]]
<strong>Output:</strong> 2 
<strong>Explanation: </strong>In the picture above, the grid on the left is grid1 and the grid on the right is grid2.
The 1s colored red in grid2 are those considered to be part of a sub-island. There are two sub-islands.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid1.length == grid2.length</code></li>
	<li><code>n == grid1[i].length == grid2[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>grid1[i][j]</code> and <code>grid2[i][j]</code> are either <code>0</code> or <code>1</code>.</li>
</ul>
 instead-->
<p>给你两个 <code>m x n</code> 的二进制矩阵 <code>grid1</code> 和 <code>grid2</code> ，它们只包含 <code>0</code> （表示水域）和 <code>1</code> （表示陆地）。一个 <strong>岛屿</strong> 是由 <strong>四个方向</strong> （水平或者竖直）上相邻的 <code>1</code> 组成的区域。任何矩阵以外的区域都视为水域。</p>

<p>如果 <code>grid2</code> 的一个岛屿，被 <code>grid1</code> 的一个岛屿 <strong>完全</strong> 包含，也就是说 <code>grid2</code> 中该岛屿的每一个格子都被 <code>grid1</code> 中同一个岛屿完全包含，那么我们称 <code>grid2</code> 中的这个岛屿为 <strong>子岛屿</strong> 。</p>

<p>请你返回 <code>grid2</code> 中 <strong>子岛屿</strong> 的 <strong>数目</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/10/test1.png" style="width: 493px; height: 205px;">
<pre><b>输入：</b>grid1 = [[1,1,1,0,0],[0,1,1,1,1],[0,0,0,0,0],[1,0,0,0,0],[1,1,0,1,1]], grid2 = [[1,1,1,0,0],[0,0,1,1,1],[0,1,0,0,0],[1,0,1,1,0],[0,1,0,1,0]]
<b>输出：</b>3
<strong>解释：</strong>如上图所示，左边为 grid1 ，右边为 grid2 。
grid2 中标红的 1 区域是子岛屿，总共有 3 个子岛屿。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/03/testcasex2.png" style="width: 491px; height: 201px;">
<pre><b>输入：</b>grid1 = [[1,0,1,0,1],[1,1,1,1,1],[0,0,0,0,0],[1,1,1,1,1],[1,0,1,0,1]], grid2 = [[0,0,0,0,0],[1,1,1,1,1],[0,1,0,1,0],[0,1,0,1,0],[1,0,0,0,1]]
<b>输出：</b>2 
<strong>解释：</strong>如上图所示，左边为 grid1 ，右边为 grid2 。
grid2 中标红的 1 区域是子岛屿，总共有 2 个子岛屿。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == grid1.length == grid2.length</code></li>
	<li><code>n == grid1[i].length == grid2[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>grid1[i][j]</code> 和 <code>grid2[i][j]</code> 都要么是 <code>0</code> 要么是 <code>1</code> 。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 35 ms

```java
class Solution {
    int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
    int m, n;
    public int countSubIslands(int[][] grid1, int[][] grid2) {
        m = grid1.length; n = grid1[0].length;
        int ans = 0;
        for (int i = 0; i < m; i++) { //找出grid2的所有岛屿的点集
            for (int j = 0; j < n; j++) {
                if (grid2[i][j] == 1) {
                    List<Integer> island = new ArrayList<>();
                    dfs(i, j, island, grid2);
                    boolean flag = true; //标记该岛屿是否为子岛屿
                    for (int index : island) { //若该岛屿的所有点在grid1中都有对应的点，则说明该岛屿是子岛屿
                        if (grid1[index / n][index % n] != 1) { //该岛屿有一个点在grid1中没有对应的点
                            flag = false; //说明该岛屿不是子岛屿
                            break;
                        }
                    }
                    if (flag) ans++;
                }
            }
        }
        return ans;
    }
    void dfs(int x, int y, List<Integer> island, int[][] grid) { //添加该岛屿其所有相关的点
        if (x < 0 || y < 0 || x >= m || y >= n || grid[x][y] == 0) return;
        island.add(x * n + y);
        grid[x][y] = 0; //搜索过的点直接设为0即可，这样同样可以避免重复访问，而不需开visit数组标记
        for (int i = 0; i < 4; i++) {
            int dx = x + dirs[i][0], dy = y + dirs[i][1];
            dfs(dx, dy, island, grid);
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/count-sub-islands/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/count-sub-islands/description/)

Solution: [LeetCode](https://leetcode.com/articles/count-sub-islands/)  /  [LeetCode中国](https://leetcode-cn.com/articles/count-sub-islands/)

[回到目录](../README.md)