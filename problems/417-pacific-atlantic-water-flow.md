# 417. pacific-atlantic-water-flow | 太平洋大西洋水流问题

## Question description

<!--If you want to use the English description, use <p>There is an <code>m x n</code> rectangular island that borders both the <strong>Pacific Ocean</strong> and <strong>Atlantic Ocean</strong>. The <strong>Pacific Ocean</strong> touches the island&#39;s left and top edges, and the <strong>Atlantic Ocean</strong> touches the island&#39;s right and bottom edges.</p>

<p>The island is partitioned into a grid of square cells. You are given an <code>m x n</code> integer matrix <code>heights</code> where <code>heights[r][c]</code> represents the <strong>height above sea level</strong> of the cell at coordinate <code>(r, c)</code>.</p>

<p>The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell&#39;s height is <strong>less than or equal to</strong> the current cell&#39;s height. Water can flow from any cell adjacent to an ocean into the ocean.</p>

<p>Return <em>a <strong>2D list</strong> of grid coordinates </em><code>result</code><em> where </em><code>result[i] = [r<sub>i</sub>, c<sub>i</sub>]</code><em> denotes that rain water can flow from cell </em><code>(r<sub>i</sub>, c<sub>i</sub>)</code><em> to <strong>both</strong> the Pacific and Atlantic oceans</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/08/waterflow-grid.jpg" style="width: 573px; height: 573px;" />
<pre>
<strong>Input:</strong> heights = [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
<strong>Output:</strong> [[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> heights = [[2,1],[1,2]]
<strong>Output:</strong> [[0,0],[0,1],[1,0],[1,1]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == heights.length</code></li>
	<li><code>n == heights[r].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 200</code></li>
	<li><code>0 &lt;= heights[r][c] &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>给定一个 <code>m x n</code> 的非负整数矩阵来表示一片大陆上各个单元格的高度。&ldquo;太平洋&rdquo;处于大陆的左边界和上边界，而&ldquo;大西洋&rdquo;处于大陆的右边界和下边界。</p>

<p>规定水流只能按照上、下、左、右四个方向流动，且只能从高到低或者在同等高度上流动。</p>

<p>请找出那些水流既可以流动到&ldquo;太平洋&rdquo;，又能流动到&ldquo;大西洋&rdquo;的陆地单元的坐标。</p>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li>输出坐标的顺序不重要</li>
	<li><em>m</em> 和 <em>n</em> 都小于150</li>
</ol>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<p>&nbsp;</p>

<pre>
给定下面的 5x5 矩阵:

  太平洋 ~   ~   ~   ~   ~ 
       ~  1   2   2   3  (5) *
       ~  3   2   3  (4) (4) *
       ~  2   4  (5)  3   1  *
       ~ (6) (7)  1   4   5  *
       ~ (5)  1   1   2   4  *
          *   *   *   *   * 大西洋

返回:

[[0, 4], [1, 3], [1, 4], [2, 2], [3, 0], [3, 1], [4, 0]] (上图中带括号的单元).
</pre>

<p>&nbsp;</p>




## Solution

Language: **java**  /  Runtime: 4 ms

```java

    public class Solution {
    private static int[][] dires = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
    private int m, n;
    private int[][] matrix;

    public List<List<Integer>> pacificAtlantic(int[][] matrix) {
        List<List<Integer>> res = new ArrayList<>();
        m = matrix.length;
        if (m == 0)
            return res;
        n = matrix[0].length;
        if (n == 0)
            return res;
        this.matrix = matrix;
        boolean[][] canReachP = new boolean[m][n];
        boolean[][] canReachA = new boolean[m][n];
        for (int i = 0; i < n; i++) {
            dfs(0, i, canReachP);
            dfs(m - 1, i, canReachA);
        }
        for (int i = 0; i < m; i++) {
            dfs(i, 0, canReachP);
            dfs(i, n - 1, canReachA);
        }
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(canReachA[i][j] && canReachP[i][j]){
                    List<Integer> temp = new ArrayList<>();
                    temp.add(i);
                    temp.add(j);
                    res.add(temp);
                }
            }
        }
        return res;
    }
    /**
     * 换一种思路，从边界往里面走，只能走到比自己更高或者等高的地方。边界能走到的地方，就是能流入对应海洋的地方。
     */
    private void dfs(int x, int y, boolean[][] canReach) {
        canReach[x][y] = true;
        for (int i = 0; i < 4; i++) {
            int newX = x + dires[i][0];
            int newY = y + dires[i][1];
            if (isIn(newX, newY) && matrix[x][y] <= matrix[newX][newY] && !canReach[newX][newY]) {
                dfs(newX, newY, canReach);
            }
        }
    }

    private boolean isIn(int x, int y) {
        return x >= 0 && x < m && y >= 0 && y < n;
    }
}



```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/pacific-atlantic-water-flow/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/pacific-atlantic-water-flow/description/)

Solution: [LeetCode](https://leetcode.com/articles/pacific-atlantic-water-flow/)  /  [LeetCode中国](https://leetcode-cn.com/articles/pacific-atlantic-water-flow/)

[回到目录](../README.md)