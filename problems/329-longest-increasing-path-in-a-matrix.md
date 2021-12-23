# 329. longest-increasing-path-in-a-matrix | 矩阵中的最长递增路径

## Question description

<!--If you want to use the English description, use <p>Given an <code>m x n</code> integers <code>matrix</code>, return <em>the length of the longest increasing path in </em><code>matrix</code>.</p>

<p>From each cell, you can either move in four directions: left, right, up, or down. You <strong>may not</strong> move <strong>diagonally</strong> or move <strong>outside the boundary</strong> (i.e., wrap-around is not allowed).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/05/grid1.jpg" style="width: 242px; height: 242px;" />
<pre>
<strong>Input:</strong> matrix = [[9,9,4],[6,6,8],[2,1,1]]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The longest increasing path is <code>[1, 2, 6, 9]</code>.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/27/tmp-grid.jpg" style="width: 253px; height: 253px;" />
<pre>
<strong>Input:</strong> matrix = [[3,4,5],[3,2,6],[2,2,1]]
<strong>Output:</strong> 4
<strong>Explanation: </strong>The longest increasing path is <code>[3, 4, 5, 6]</code>. Moving diagonally is not allowed.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> matrix = [[1]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 200</code></li>
	<li><code>0 &lt;= matrix[i][j] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给定一个 <code>m x n</code> 整数矩阵 <code>matrix</code> ，找出其中 <strong>最长递增路径</strong> 的长度。</p>

<p>对于每个单元格，你可以往上，下，左，右四个方向移动。 你 <strong>不能</strong> 在 <strong>对角线</strong> 方向上移动或移动到 <strong>边界外</strong>（即不允许环绕）。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/05/grid1.jpg" style="width: 242px; height: 242px;" />
<pre>
<strong>输入：</strong>matrix = [[9,9,4],[6,6,8],[2,1,1]]
<strong>输出：</strong>4 
<strong>解释：</strong>最长递增路径为 <code>[1, 2, 6, 9]</code>。</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/01/27/tmp-grid.jpg" style="width: 253px; height: 253px;" />
<pre>
<strong>输入：</strong>matrix = [[3,4,5],[3,2,6],[2,2,1]]
<strong>输出：</strong>4 
<strong>解释：</strong>最长递增路径是 <code>[3, 4, 5, 6]</code>。注意不允许在对角线方向上移动。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>matrix = [[1]]
<strong>输出：</strong>1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 <= m, n <= 200</code></li>
	<li><code>0 <= matrix[i][j] <= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public int longestIncreasingPath(int[][] matrix) {
        int m=matrix.length,n=matrix[0].length;
        int ans=1;
        int[][]memo=new int[m][n];
        //Arrays.fill(memo,0);
        boolean[][]vis=new boolean[matrix.length][matrix[0].length];
        for(int i=0;i<matrix.length;i++){
            for(int j=0;j<matrix[0].length;j++){
                ans=Math.max(ans,dfs(i,j,matrix,vis,memo));
            }
        }
        return ans;
    }
    public int dfs(int i,int j,int[][] matrix,boolean[][]vis,int[][]memo){
        if(memo[i][j]!=0)return memo[i][j];
        if(i<0||j<0||i>matrix.length||j>matrix[0].length||vis[i][j])return 0;
        int m=matrix.length,n=matrix[0].length;
        int res=1,t1=0,t2=0,t3=0,t4=0;
        vis[i][j]=true;
        if((i-1)>=0&&!vis[i-1][j]&&matrix[i-1][j]>matrix[i][j]) {
            t1 = dfs(i - 1, j, matrix, vis,memo);
        }
        if((i+1)<m&&!vis[i+1][j]&&matrix[i+1][j]>matrix[i][j]) {
            t2 = dfs(i + 1, j, matrix, vis,memo);
        }
        if((j-1)>=0&&!vis[i][j-1]&&matrix[i][j-1]>matrix[i][j]) {
            t3 = dfs(i, j - 1, matrix, vis,memo);
        }
        if((j+1)<n&&!vis[i][j+1]&&matrix[i][j+1]>matrix[i][j]) {
            t4 = dfs(i, j + 1, matrix, vis,memo);
        }
        vis[i][j]=false;
        memo[i][j]=res+Math.max(Math.max(t1,t2),Math.max(t3,t4));
        return res+Math.max(Math.max(t1,t2),Math.max(t3,t4));
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/longest-increasing-path-in-a-matrix/description/)

Solution: [LeetCode](https://leetcode.com/articles/longest-increasing-path-in-a-matrix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/longest-increasing-path-in-a-matrix/)

[回到目录](../README.md)