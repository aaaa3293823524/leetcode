# 62. unique-paths | 不同路径

## Question description

<!--If you want to use the English description, use <p>A robot is located at the top-left corner of a <code>m x n</code> grid (marked &#39;Start&#39; in the diagram below).</p>

<p>The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked &#39;Finish&#39; in the diagram below).</p>

<p>How many possible unique paths are there?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img src="https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png" style="width: 400px; height: 183px;" />
<pre>
<strong>Input:</strong> m = 3, n = 7
<strong>Output:</strong> 28
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> m = 3, n = 2
<strong>Output:</strong> 3
<strong>Explanation:</strong>
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -&gt; Down -&gt; Down
2. Down -&gt; Down -&gt; Right
3. Down -&gt; Right -&gt; Down
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> m = 7, n = 3
<strong>Output:</strong> 28
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> m = 3, n = 3
<strong>Output:</strong> 6
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li>It&#39;s guaranteed that the answer will be less than or equal to <code>2 * 10<sup>9</sup></code>.</li>
</ul>
 instead-->
<p>一个机器人位于一个 <em>m x n </em>网格的左上角 （起始点在下图中标记为&ldquo;Start&rdquo; ）。</p>

<p>机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为&ldquo;Finish&rdquo;）。</p>

<p>问总共有多少条不同的路径？</p>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/robot_maze.png"></p>

<p><small>例如，上图是一个7 x 3 的网格。有多少可能的路径？</small></p>

<p>&nbsp;</p>

<p><strong>示例&nbsp;1:</strong></p>

<pre><strong>输入:</strong> m = 3, n = 2
<strong>输出:</strong> 3
<strong>解释:</strong>
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -&gt; 向右 -&gt; 向下
2. 向右 -&gt; 向下 -&gt; 向右
3. 向下 -&gt; 向右 -&gt; 向右
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre><strong>输入:</strong> m = 7, n = 3
<strong>输出:</strong> 28</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li>题目数据保证答案小于等于 <code>2 * 10 ^ 9</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int uniquePaths(int m, int n) {
        int[][] dp = new int[m][n];
        for (int i = 0; i < n; i++) dp[0][i] = 1;
        for (int i = 0; i < m; i++) dp[i][0] = 1;
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
            }
        }
        return dp[m - 1][n - 1];  
    }
}


```

Language: **python3**  /  Runtime: 48 ms

```python3
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        return int(math.factorial(m+n-2)/math.factorial(m-1)/math.factorial(n-1))


        
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/unique-paths/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/unique-paths/description/)

Solution: [LeetCode](https://leetcode.com/articles/unique-paths/)  /  [LeetCode中国](https://leetcode-cn.com/articles/unique-paths/)

[回到目录](../README.md)