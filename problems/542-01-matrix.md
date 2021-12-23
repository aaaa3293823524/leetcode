# 542. 01-matrix | 01 矩阵

## Question description

<!--If you want to use the English description, use <p>Given an <code>m x n</code> binary matrix <code>mat</code>, return <em>the distance of the nearest </em><code>0</code><em> for each cell</em>.</p>

<p>The distance between two adjacent cells is <code>1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/24/01-1-grid.jpg" style="width: 253px; height: 253px;" />
<pre>
<strong>Input:</strong> mat = [[0,0,0],[0,1,0],[0,0,0]]
<strong>Output:</strong> [[0,0,0],[0,1,0],[0,0,0]]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/24/01-2-grid.jpg" style="width: 253px; height: 253px;" />
<pre>
<strong>Input:</strong> mat = [[0,0,0],[0,1,0],[1,1,1]]
<strong>Output:</strong> [[0,0,0],[0,1,0],[1,2,1]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= m * n &lt;= 10<sup>4</sup></code></li>
	<li><code>mat[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
	<li>There is at least one <code>0</code> in <code>mat</code>.</li>
</ul>
 instead-->
<p>给定一个由 <code>0</code> 和 <code>1</code> 组成的矩阵 <code>mat</code> ，请输出一个大小相同的矩阵，其中每一个格子是 <code>mat</code> 中对应位置元素到最近的 <code>0</code> 的距离。</p>

<p>两个相邻元素间的距离为 <code>1</code> 。</p>

<p> </p>

<p><b>示例 1：</b></p>

<p><img alt="" src="https://pic.leetcode-cn.com/1626667201-NCWmuP-image.png" style="width: 150px; " /></p>

<pre>
<strong>输入：</strong>mat =<strong> </strong>[[0,0,0],[0,1,0],[0,0,0]]
<strong>输出：</strong>[[0,0,0],[0,1,0],[0,0,0]]
</pre>

<p><b>示例 2：</b></p>

<p><img alt="" src="https://pic.leetcode-cn.com/1626667205-xFxIeK-image.png" style="width: 150px; " /></p>

<pre>
<b>输入：</b>mat =<b> </b>[[0,0,0],[0,1,0],[1,1,1]]
<strong>输出：</strong>[[0,0,0],[0,1,0],[1,2,1]]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 <= m, n <= 10<sup>4</sup></code></li>
	<li><code>1 <= m * n <= 10<sup>4</sup></code></li>
	<li><code>mat[i][j] is either 0 or 1.</code></li>
	<li><code>mat</code> 中至少有一个 <code>0 </code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 14 ms

```java
class Solution {
    public int[][] updateMatrix(int[][] mat) {
        int n=mat.length,m=mat[0].length;
        boolean[][]vis=new boolean[n][m];
        Queue<int[]>queue=new LinkedList<int[]>();
        int[][] dist = new int[n][m];
        
        int direction[][]= {{0,1},{0,-1},{1,0},{-1,0}};
        int dirIndex=0;
        for(int i=0;i<n;i++) {
            for(int j=0;j<m;j++) {
                if(mat[i][j]==0) {
                    vis[i][j]=true;
                    queue.offer(new int[] {i,j});
                }
            }
        }
        while(!queue.isEmpty()) {
            int[]num=queue.poll();
            int r=num[0],c=num[1];
            dirIndex=0;
            for(int i=0;i<4;i++) {
                int newR=r+direction[dirIndex+i][0];
                int newC=c+direction[dirIndex+i][1];
                if(newR>=0&&newR<n&&newC>=0&&newC<m&&!vis[newR][newC]) {
                    dist[newR][newC]=dist[r][c]+1;
                    queue.offer(new int[] {newR,newC});
                    vis[newR][newC]=true;
                }
            }
        }
        
        return dist;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/01-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/01-matrix/description/)

Solution: [LeetCode](https://leetcode.com/articles/01-matrix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/01-matrix/)

[回到目录](../README.md)