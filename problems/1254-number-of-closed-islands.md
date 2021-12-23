# 1254. number-of-closed-islands | 统计封闭岛屿的数目

## Question description

<!--If you want to use the English description, use <p>Given a 2D&nbsp;<code>grid</code> consists of <code>0s</code> (land)&nbsp;and <code>1s</code> (water).&nbsp; An <em>island</em> is a maximal 4-directionally connected group of <code><font face="monospace">0</font>s</code> and a <em>closed island</em>&nbsp;is an island <strong>totally</strong>&nbsp;(all left, top, right, bottom) surrounded by <code>1s.</code></p>

<p>Return the number of <em>closed islands</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/10/31/sample_3_1610.png" style="width: 240px; height: 120px;" /></p>

<pre>
<strong>Input:</strong> grid = [[1,1,1,1,1,1,1,0],[1,0,0,0,0,1,1,0],[1,0,1,0,1,1,1,0],[1,0,0,0,0,1,0,1],[1,1,1,1,1,1,1,0]]
<strong>Output:</strong> 2
<strong>Explanation:</strong> 
Islands in gray are closed because they are completely surrounded by water (group of 1s).</pre>

<p><strong>Example 2:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/10/31/sample_4_1610.png" style="width: 160px; height: 80px;" /></p>

<pre>
<strong>Input:</strong> grid = [[0,0,1,0,0],[0,1,0,1,0],[0,1,1,1,0]]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1,1,1,1,1,1,1],
&nbsp;              [1,0,0,0,0,0,1],
&nbsp;              [1,0,1,1,1,0,1],
&nbsp;              [1,0,1,0,1,0,1],
&nbsp;              [1,0,1,1,1,0,1],
&nbsp;              [1,0,0,0,0,0,1],
               [1,1,1,1,1,1,1]]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= grid.length, grid[0].length &lt;= 100</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;=1</code></li>
</ul>
 instead-->
<p>有一个二维矩阵 <code>grid</code>&nbsp;，每个位置要么是陆地（记号为&nbsp;<code>0</code> ）要么是水域（记号为&nbsp;<code>1</code> ）。</p>

<p>我们从一块陆地出发，每次可以往上下左右&nbsp;4 个方向相邻区域走，能走到的所有陆地区域，我们将其称为一座「<strong>岛屿</strong>」。</p>

<p>如果一座岛屿&nbsp;<strong>完全</strong>&nbsp;由水域包围，即陆地边缘上下左右所有相邻区域都是水域，那么我们将其称为 「<strong>封闭岛屿</strong>」。</p>

<p>请返回封闭岛屿的数目。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/11/07/sample_3_1610.png"></p>

<pre><strong>输入：</strong>grid = [[1,1,1,1,1,1,1,0],[1,0,0,0,0,1,1,0],[1,0,1,0,1,1,1,0],[1,0,0,0,0,1,0,1],[1,1,1,1,1,1,1,0]]
<strong>输出：</strong>2
<strong>解释：</strong>
灰色区域的岛屿是封闭岛屿，因为这座岛屿完全被水域包围（即被 1 区域包围）。</pre>

<p><strong>示例 2：</strong></p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/11/07/sample_4_1610.png"></p>

<pre><strong>输入：</strong>grid = [[0,0,1,0,0],[0,1,0,1,0],[0,1,1,1,0]]
<strong>输出：</strong>1
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>grid = [[1,1,1,1,1,1,1],
&nbsp;            [1,0,0,0,0,0,1],
&nbsp;            [1,0,1,1,1,0,1],
&nbsp;            [1,0,1,0,1,0,1],
&nbsp;            [1,0,1,1,1,0,1],
&nbsp;            [1,0,0,0,0,0,1],
             [1,1,1,1,1,1,1]]
<strong>输出：</strong>2
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= grid.length, grid[0].length &lt;= 100</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;=1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 116 ms

```java
class Solution {
    public int closedIsland(int[][] grid) {
        int m=grid.length,n=grid[0].length;
        for(int i=0;i<m;i++){
            if(grid[i][0]==0)dfs1(i,0,grid);
            if(grid[i][n-1]==0)dfs1(i,n-1,grid);
        }
        for(int i=0;i<n;i++){
            if(grid[0][i]==0)
                dfs1(0,i,grid);
            if(grid[m-1][i]==0)dfs1(m-1,i,grid);
        }
        int count=0;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                System.out.print(grid[i][j]+"");
            }
            System.out.println();
        }
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(grid[i][j]==0){
                    count++;
                    dfs1(i,j,grid);
                }
            }
        }
        return count;
    }
    public void dfs1(int i,int j,int[][] grid){
        int m=grid.length,n=grid[0].length;
        //System.out.println(i+" : "+j);
        if(i<0||j<0||i>=m||j>=n||grid[i][j]!=0)return;
        //System.out.print("ss");
        grid[i][j]=1;
        dfs1(i,j+1,grid);
        dfs1(i,j-1,grid);
        dfs1(i-1,j,grid);
        dfs1(i+1,j,grid);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-closed-islands/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-closed-islands/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-closed-islands/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-closed-islands/)

[回到目录](../README.md)