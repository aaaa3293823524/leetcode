# 剑指 Offer II 107. 2bCMpM | 矩阵中的距离

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个由 <code>0</code> 和 <code>1</code> 组成的矩阵 <code>mat</code>&nbsp;，请输出一个大小相同的矩阵，其中每一个格子是 <code>mat</code> 中对应位置元素到最近的 <code>0</code> 的距离。</p>

<p>两个相邻元素间的距离为 <code>1</code> 。</p>

<p>&nbsp;</p>

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

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= m * n &lt;= 10<sup>4</sup></code></li>
	<li><code>mat[i][j] is either 0 or 1.</code></li>
	<li><code>mat</code> 中至少有一个 <code>0&nbsp;</code></li>
</ul>

<p>&nbsp;</p>

<p><meta charset="UTF-8" />注意：本题与主站 542&nbsp;题相同：<a href="https://leetcode-cn.com/problems/01-matrix/">https://leetcode-cn.com/problems/01-matrix/</a></p>




## Solution

Language: **java**  /  Runtime: 14 ms

```java
class Solution {
    public int[][] updateMatrix(int[][] mat) {
        Queue<int[]>queue=new LinkedList<>();
        int m=mat.length,n=mat[0].length;
        boolean[][]vis=new boolean[m][n];
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(mat[i][j]==0){
                    queue.offer(new int[]{i,j});
                    vis[i][j]=true;
                }
            }
        }
        int ans=0;
        int[][]directions={{1,0},{-1,0},{0,1},{0,-1}};
        while(!queue.isEmpty()){
            ans++;
            int size=queue.size();
            for(int i=0;i<size;i++){
                int[]nums=queue.poll();
                for(int j=0;j<4;j++){
                    int newX=nums[0]+directions[j][0];
                    int newY=nums[1]+directions[j][1];
                    if(newX>=0&&newX<m&&newY>=0&&newY<n&&!vis[newX][newY]){
                        vis[newX][newY]=true;
                        mat[newX][newY]=ans;
                        queue.offer(new int[]{newX,newY});
                    }
                }
            }
        }
        return mat;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/2bCMpM/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/2bCMpM/description/)

Solution: [LeetCode](https://leetcode.com/articles/2bCMpM/)  /  [LeetCode中国](https://leetcode-cn.com/articles/2bCMpM/)

[回到目录](../README.md)