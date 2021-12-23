# 63. unique-paths-ii | 不同路径 II

## Question description

<!--If you want to use the English description, use <p>A robot is located at the top-left corner of a <code>m x n</code> grid (marked &#39;Start&#39; in the diagram below).</p>

<p>The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked &#39;Finish&#39; in the diagram below).</p>

<p>Now consider if some obstacles are added to the grids. How many unique paths would there be?</p>

<p>An obstacle and space is marked as <code>1</code> and <code>0</code> respectively in the grid.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/robot1.jpg" style="width: 242px; height: 242px;" />
<pre>
<strong>Input:</strong> obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
<strong>Output:</strong> 2
<strong>Explanation:</strong> There is one obstacle in the middle of the 3x3 grid above.
There are two ways to reach the bottom-right corner:
1. Right -&gt; Right -&gt; Down -&gt; Down
2. Down -&gt; Down -&gt; Right -&gt; Right
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/robot2.jpg" style="width: 162px; height: 162px;" />
<pre>
<strong>Input:</strong> obstacleGrid = [[0,1],[0,0]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m ==&nbsp;obstacleGrid.length</code></li>
	<li><code>n ==&nbsp;obstacleGrid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li><code>obstacleGrid[i][j]</code> is <code>0</code> or <code>1</code>.</li>
</ul>
 instead-->
<p>一个机器人位于一个 <em>m x n </em>网格的左上角 （起始点在下图中标记为“Start” ）。</p>

<p>机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。</p>

<p>现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/robot_maze.png" style="height: 183px; width: 400px;" /></p>

<p>网格中的障碍物和空位置分别用 <code>1</code> 和 <code>0</code> 来表示。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/robot1.jpg" style="width: 242px; height: 242px;" />
<pre>
<strong>输入：</strong>obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
<strong>输出：</strong>2
<strong>解释：</strong>
3x3 网格的正中间有一个障碍物。
从左上角到右下角一共有 <code>2</code> 条不同的路径：
1. 向右 -> 向右 -> 向下 -> 向下
2. 向下 -> 向下 -> 向右 -> 向右
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/robot2.jpg" style="width: 162px; height: 162px;" />
<pre>
<strong>输入：</strong>obstacleGrid = [[0,1],[0,0]]
<strong>输出：</strong>1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == obstacleGrid.length</code></li>
	<li><code>n == obstacleGrid[i].length</code></li>
	<li><code>1 <= m, n <= 100</code></li>
	<li><code>obstacleGrid[i][j]</code> 为 <code>0</code> 或 <code>1</code></li>
</ul>


## Note

「滚动数组思想」是一种常见的动态规划优化方法，在我们的题目中已经多次使用到，例如「剑指 Offer 46. 把数字翻译成字符串」、「70. 爬楼梯」等，当我们定义的状态在动态规划的转移方程中只和某几个状态相关的时候，就可以考虑这种优化方法，目的是给空间复杂度「降维」。如果你还不知道什么是「滚动数组思想」，一定要查阅相关资料进行学习哦。



动态规划的题目分为两大类，一种是求最优解类，典型问题是背包问题，另一种就是计数类，比如这里的统计方案数的问题，它们都存在一定的递推性质。前者的递推性质还有一个名字，叫做 「最优子结构」 ——即当前问题的最优解取决于子问题的最优解，后者类似，当前问题的方案数取决于子问题的方案数。所以在遇到求方案数的问题时，我们可以往动态规划的方向考虑。



这类动态规划的题目在题库中也出现过多次，例如「221. 最大正方形」、「1162. 地图分析」等。他们都以二维坐标作为状态，大多数都可以使用滚动数组进行优化。如果我们熟悉这类问题，可以一眼看出这是一个动态规划问题



复杂度分析



时间复杂度：O(nm)O(nm)，其中 nn 为网格的行数，mm 为网格的列数。我们只需要遍历所有网格一次即可。

空间复杂度：O(m)O(m)。利用滚动数组优化，我们可以只用 O(m)O(m) 大小的空间来记录当前行的 f 值。








## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m=obstacleGrid.length,n=obstacleGrid[0].length;
        if(m==0||n==0||obstacleGrid[0][0]==1)return 0;
        int[][]dp=new int[m][n];
        dp[0][0]=1;
        for(int i=1;i<m;i++){
            if(obstacleGrid[i][0]==1)dp[i][0]=0;
            else{
                dp[i][0]=dp[i-1][0];
            }
        }
        for(int i=1;i<n;i++){
            if(obstacleGrid[0][i]==1)dp[0][i]=0;
            else {
                dp[0][i] = dp[0][i-1];
            }
        }
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                if(obstacleGrid[i][j]==1)dp[i][j]=0;
                else{
                    dp[i][j]=dp[i-1][j]+dp[i][j-1];
                }
            }
        }
        return dp[m-1][n-1];
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/unique-paths-ii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/unique-paths-ii/description/)

Solution: [LeetCode](https://leetcode.com/articles/unique-paths-ii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/unique-paths-ii/)

[回到目录](../README.md)