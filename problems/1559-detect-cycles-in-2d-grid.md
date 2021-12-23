# 1559. detect-cycles-in-2d-grid | 二维网格图中探测环

## Question description

<!--If you want to use the English description, use <p>Given a 2D array of characters <code>grid</code> of size <code>m x n</code>, you need to find if there exists any cycle consisting of the <strong>same value</strong> in <code>grid</code>.</p>

<p>A cycle is a path of <strong>length 4 or more</strong> in the grid that starts and ends at the same cell. From a given cell, you can move to one of the cells adjacent to it - in one of the four directions (up, down, left, or right), if it has the <strong>same value</strong> of the current cell.</p>

<p>Also, you cannot move to the cell that you visited in your last move. For example, the cycle <code>(1, 1) -&gt; (1, 2) -&gt; (1, 1)</code> is invalid because from <code>(1, 2)</code> we visited <code>(1, 1)</code> which was the last visited cell.</p>

<p>Return <code>true</code> if any cycle of the same value exists in <code>grid</code>, otherwise, return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2020/07/15/1.png" style="width: 231px; height: 152px;" /></strong></p>

<pre>
<strong>Input:</strong> grid = [[&quot;a&quot;,&quot;a&quot;,&quot;a&quot;,&quot;a&quot;],[&quot;a&quot;,&quot;b&quot;,&quot;b&quot;,&quot;a&quot;],[&quot;a&quot;,&quot;b&quot;,&quot;b&quot;,&quot;a&quot;],[&quot;a&quot;,&quot;a&quot;,&quot;a&quot;,&quot;a&quot;]]
<strong>Output:</strong> true
<strong>Explanation: </strong>There are two valid cycles shown in different colors in the image below:
<img alt="" src="https://assets.leetcode.com/uploads/2020/07/15/11.png" style="width: 225px; height: 163px;" />
</pre>

<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2020/07/15/22.png" style="width: 236px; height: 154px;" /></strong></p>

<pre>
<strong>Input:</strong> grid = [[&quot;c&quot;,&quot;c&quot;,&quot;c&quot;,&quot;a&quot;],[&quot;c&quot;,&quot;d&quot;,&quot;c&quot;,&quot;c&quot;],[&quot;c&quot;,&quot;c&quot;,&quot;e&quot;,&quot;c&quot;],[&quot;f&quot;,&quot;c&quot;,&quot;c&quot;,&quot;c&quot;]]
<strong>Output:</strong> true
<strong>Explanation: </strong>There is only one valid cycle highlighted in the image below:
<img alt="" src="https://assets.leetcode.com/uploads/2020/07/15/2.png" style="width: 229px; height: 157px;" />
</pre>

<p><strong>Example 3:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2020/07/15/3.png" style="width: 183px; height: 120px;" /></strong></p>

<pre>
<strong>Input:</strong> grid = [[&quot;a&quot;,&quot;b&quot;,&quot;b&quot;],[&quot;b&quot;,&quot;z&quot;,&quot;b&quot;],[&quot;b&quot;,&quot;b&quot;,&quot;a&quot;]]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>grid</code> consists only of lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个二维字符网格数组&nbsp;<code>grid</code>&nbsp;，大小为&nbsp;<code>m x n</code>&nbsp;，你需要检查&nbsp;<code>grid</code>&nbsp;中是否存在 <strong>相同值</strong> 形成的环。</p>

<p>一个环是一条开始和结束于同一个格子的长度 <strong>大于等于 4</strong>&nbsp;的路径。对于一个给定的格子，你可以移动到它上、下、左、右四个方向相邻的格子之一，可以移动的前提是这两个格子有 <strong>相同的值&nbsp;</strong>。</p>

<p>同时，你也不能回到上一次移动时所在的格子。比方说，环&nbsp;&nbsp;<code>(1, 1) -&gt; (1, 2) -&gt; (1, 1)</code>&nbsp;是不合法的，因为从 <code>(1, 2)</code>&nbsp;移动到 <code>(1, 1)</code> 回到了上一次移动时的格子。</p>

<p>如果 <code>grid</code>&nbsp;中有相同值形成的环，请你返回 <code>true</code>&nbsp;，否则返回 <code>false</code>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/22/5482e1.png" style="height: 152px; width: 231px;"></strong></p>

<pre><strong>输入：</strong>grid = [[&quot;a&quot;,&quot;a&quot;,&quot;a&quot;,&quot;a&quot;],[&quot;a&quot;,&quot;b&quot;,&quot;b&quot;,&quot;a&quot;],[&quot;a&quot;,&quot;b&quot;,&quot;b&quot;,&quot;a&quot;],[&quot;a&quot;,&quot;a&quot;,&quot;a&quot;,&quot;a&quot;]]
<strong>输出：</strong>true
<strong>解释：</strong>如下图所示，有 2 个用不同颜色标出来的环：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/22/5482e11.png" style="height: 163px; width: 225px;">
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/22/5482e2.png" style="height: 154px; width: 236px;"></strong></p>

<pre><strong>输入：</strong>grid = [[&quot;c&quot;,&quot;c&quot;,&quot;c&quot;,&quot;a&quot;],[&quot;c&quot;,&quot;d&quot;,&quot;c&quot;,&quot;c&quot;],[&quot;c&quot;,&quot;c&quot;,&quot;e&quot;,&quot;c&quot;],[&quot;f&quot;,&quot;c&quot;,&quot;c&quot;,&quot;c&quot;]]
<strong>输出：</strong>true
<strong>解释：</strong>如下图所示，只有高亮所示的一个合法环：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/22/5482e22.png" style="height: 157px; width: 229px;">
</pre>

<p><strong>示例 3：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/08/22/5482e3.png" style="height: 120px; width: 183px;"></strong></p>

<pre><strong>输入：</strong>grid = [[&quot;a&quot;,&quot;b&quot;,&quot;b&quot;],[&quot;b&quot;,&quot;z&quot;,&quot;b&quot;],[&quot;b&quot;,&quot;b&quot;,&quot;a&quot;]]
<strong>输出：</strong>false
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m &lt;= 500</code></li>
	<li><code>1 &lt;= n &lt;= 500</code></li>
	<li><code>grid</code>&nbsp;只包含小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 19 ms

```java
class Solution {
    int[][] dirs = {{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
    int m, n;
    boolean[][] visit;
    public boolean containsCycle(char[][] grid) {
        m = grid.length; n = grid[0].length;
        visit = new boolean[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (!visit[i][j]) {
                    if (dfs(i, j, -1, -1, grid)) return true;
                }
            }
        }
        return false;
    }
    boolean dfs(int x, int y, int px, int py, char[][] grid) { //x、y表示当前坐标，dx、dy表示下一步不能到达的坐标
        if (visit[x][y]) return true;
        visit[x][y] = true;
        for (int[] dir : dirs) {
            int dx = x + dir[0], dy = y + dir[1];
            if (dx >= 0 && dx < m && dy >= 0 && dy < n && (dx != px || dy != py) && grid[dx][dy] == grid[x][y] && dfs(dx, dy, x, y, grid)) return true;
        }
        return false;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/detect-cycles-in-2d-grid/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/detect-cycles-in-2d-grid/description/)

Solution: [LeetCode](https://leetcode.com/articles/detect-cycles-in-2d-grid/)  /  [LeetCode中国](https://leetcode-cn.com/articles/detect-cycles-in-2d-grid/)

[回到目录](../README.md)