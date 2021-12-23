# 1139. largest-1-bordered-square | 最大的以 1 为边界的正方形

## Question description

<!--If you want to use the English description, use <p>Given a 2D <code>grid</code> of <code>0</code>s and <code>1</code>s, return the number of elements in&nbsp;the largest <strong>square</strong>&nbsp;subgrid that has all <code>1</code>s on its <strong>border</strong>, or <code>0</code> if such a subgrid&nbsp;doesn&#39;t exist in the <code>grid</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1,1,1],[1,0,1],[1,1,1]]
<strong>Output:</strong> 9
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1,1,0,0]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= grid.length &lt;= 100</code></li>
	<li><code>1 &lt;= grid[0].length &lt;= 100</code></li>
	<li><code>grid[i][j]</code> is <code>0</code> or <code>1</code></li>
</ul> instead-->
<p>给你一个由若干 <code>0</code> 和 <code>1</code> 组成的二维网格&nbsp;<code>grid</code>，请你找出边界全部由 <code>1</code> 组成的最大 <strong>正方形</strong> 子网格，并返回该子网格中的元素数量。如果不存在，则返回 <code>0</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>grid = [[1,1,1],[1,0,1],[1,1,1]]
<strong>输出：</strong>9
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>grid = [[1,1,0,0]]
<strong>输出：</strong>1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= grid.length &lt;= 100</code></li>
	<li><code>1 &lt;= grid[0].length &lt;= 100</code></li>
	<li><code>grid[i][j]</code> 为&nbsp;<code>0</code>&nbsp;或&nbsp;<code>1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int largest1BorderedSquare(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        //dp[i][j][0]: i,j左边连续的1的个数
        //dp[i][j][1]: i,j上边连续的1的个数
        int[][][] dp = new int[m+1][n+1][2];
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (grid[i-1][j-1] == 1){
                    dp[i][j][0] = 1 + dp[i][j-1][0];
                    dp[i][j][1] = 1 + dp[i-1][j][1];
                }
            }
        }
        int res = 0;
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                //最短的那条边不一定是合法的边长，如果该边长不合法就需要缩减边长，直到找到合法的
                for (int side = Math.min(dp[i][j][0], dp[i][j][1]); side >= 1; side--){
                    if (dp[i][j-side+1][1] >= side && dp[i-side+1][j][0] >= side){
                        res = Math.max(res, side);
                        break; //更短的就没必要考虑了
                    }
                }
            }
        }
        return res * res;
    }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/largest-1-bordered-square/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-1-bordered-square/description/)

Solution: [LeetCode](https://leetcode.com/articles/largest-1-bordered-square/)  /  [LeetCode中国](https://leetcode-cn.com/articles/largest-1-bordered-square/)

[回到目录](../README.md)