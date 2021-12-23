# 剑指 Offer 47. li-wu-de-zui-da-jie-zhi-lcof | 礼物的最大价值

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>在一个 m*n 的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值（价值大于 0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向右或者向下移动一格、直到到达棋盘的右下角。给定一个棋盘及其上面的礼物的价值，请计算你最多能拿到多少价值的礼物？</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入:</strong> 
<code>[
&nbsp; [1,3,1],
&nbsp; [1,5,1],
&nbsp; [4,2,1]
]</code>
<strong>输出:</strong> <code>12
</code><strong>解释:</strong> 路径 1&rarr;3&rarr;5&rarr;2&rarr;1 可以拿到最多价值的礼物</pre>

<p>&nbsp;</p>

<p>提示：</p>

<ul>
	<li><code>0 &lt; grid.length &lt;= 200</code></li>
	<li><code>0 &lt; grid[0].length &lt;= 200</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public int maxValue(int[][] grid) {
        int m=grid.length,n=grid[0].length;
        int [][]dp=new int[m][n];
        dp[0][0]=grid[0][0];
        for(int i=1;i<m;i++)dp[i][0]=dp[i-1][0]+grid[i][0];
        for(int i=1;i<n;i++)dp[0][i]=dp[0][i-1]+grid[0][i];
        for(int i=1;i<m;i++) {
            for(int j=1;j<n;j++) {
                dp[i][j]=Math.max(dp[i-1][j], dp[i][j-1])+grid[i][j];
            }
        }
        // for(int i=0;i<m;i++) {
        //     for(int j=0;j<n;j++) {
        //         System.out.println(dp[i][j]);
        //     }
        // }
        return dp[m-1][n-1];
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/li-wu-de-zui-da-jie-zhi-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/li-wu-de-zui-da-jie-zhi-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/li-wu-de-zui-da-jie-zhi-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/li-wu-de-zui-da-jie-zhi-lcof/)

[回到目录](../README.md)