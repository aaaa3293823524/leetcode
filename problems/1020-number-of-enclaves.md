# 1020. number-of-enclaves | 飞地的数量

## Question description

<!--If you want to use the English description, use <p>You are given an <code>m x n</code> binary matrix <code>grid</code>, where <code>0</code> represents a sea cell and <code>1</code> represents a land cell.</p>

<p>A <strong>move</strong> consists of walking from one land cell to another adjacent (<strong>4-directionally</strong>) land cell or walking off the boundary of the <code>grid</code>.</p>

<p>Return <em>the number of land cells in</em> <code>grid</code> <em>for which we cannot walk off the boundary of the grid in any number of <strong>moves</strong></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/18/enclaves1.jpg" style="width: 333px; height: 333px;" />
<pre>
<strong>Input:</strong> grid = [[0,0,0,0],[1,0,1,0],[0,1,1,0],[0,0,0,0]]
<strong>Output:</strong> 3
<strong>Explanation:</strong> There are three 1s that are enclosed by 0s, and one 1 that is not enclosed because its on the boundary.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/18/enclaves2.jpg" style="width: 333px; height: 333px;" />
<pre>
<strong>Input:</strong> grid = [[0,1,1,0],[0,0,1,0],[0,0,1,0],[0,0,0,0]]
<strong>Output:</strong> 0
<strong>Explanation:</strong> All 1s are either on the boundary or can reach the boundary.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>grid[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>
 instead-->
<p>给出一个二维数组&nbsp;<code>A</code>，每个单元格为 0（代表海）或 1（代表陆地）。</p>

<p>移动是指在陆地上从一个地方走到另一个地方（朝四个方向之一）或离开网格的边界。</p>

<p>返回网格中<strong>无法</strong>在任意次数的移动中离开网格边界的陆地单元格的数量。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[[0,0,0,0],[1,0,1,0],[0,1,1,0],[0,0,0,0]]
<strong>输出：</strong>3
<strong>解释： </strong>
有三个 1 被 0 包围。一个 1 没有被包围，因为它在边界上。</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>[[0,1,1,0],[0,0,1,0],[0,0,1,0],[0,0,0,0]]
<strong>输出：</strong>0
<strong>解释：</strong>
所有 1 都在边界上或可以到达边界。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 500</code></li>
	<li><code>1 &lt;= A[i].length &lt;= 500</code></li>
	<li><code>0 &lt;= A[i][j] &lt;= 1</code></li>
	<li>所有行的大小都相同</li>
</ol>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int numEnclaves(int[][] grid) {
        int m=grid.length,n=grid[0].length;
        for(int i=0;i<m;i++){
            if(grid[i][0]==1)
                dfs(i,0,grid);
            if(grid[i][n-1]==1)dfs(i,n-1,grid);
        }
        for(int i=0;i<n;i++){
            if(grid[0][i]==1)
                dfs(0,i,grid);
            if(grid[m-1][i]==1)dfs(m-1,i,grid);
        }
        int count=0;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]==1){
                    count++;
                    //dfs1(i,j,grid);
                }
            }
        }
        return count;
    }
    public void dfs(int i,int j,int[][] grid){
        int m=grid.length,n=grid[0].length;
        if(i<0||j<0||i>=m||j>=n||grid[i][j]!=1)return;
        grid[i][j]=0;
        dfs(i,j+1,grid);
        dfs(i,j-1,grid);
        dfs(i-1,j,grid);
        dfs(i+1,j,grid);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-enclaves/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-enclaves/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-enclaves/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-enclaves/)

[回到目录](../README.md)