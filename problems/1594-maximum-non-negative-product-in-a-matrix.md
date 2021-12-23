# 1594. maximum-non-negative-product-in-a-matrix | 矩阵的最大非负积

## Question description

<!--If you want to use the English description, use <p>You are given a&nbsp;<code>rows x cols</code>&nbsp;matrix&nbsp;<code>grid</code>.&nbsp;Initially, you&nbsp;are located at the top-left&nbsp;corner <code>(0, 0)</code>,&nbsp;and in each step, you can only <strong>move right&nbsp;or&nbsp;down</strong> in the matrix.</p>

<p>Among all possible paths starting from the top-left corner&nbsp;<code>(0, 0)</code>&nbsp;and ending in the bottom-right corner&nbsp;<code>(rows - 1, cols - 1)</code>, find the path with the&nbsp;<strong>maximum non-negative product</strong>. The product of a path is the product of all integers in the grid cells visited along the path.</p>

<p>Return the&nbsp;<em>maximum non-negative product&nbsp;<strong>modulo</strong>&nbsp;</em><code>10<sup>9</sup>&nbsp;+ 7</code>.&nbsp;<em>If the maximum product is <strong>negative</strong> return&nbsp;</em><code>-1</code>.</p>

<p><strong>Notice that the modulo is performed after getting the maximum product.</strong></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> grid = [[-1,-2,-3],
&nbsp;              [-2,-3,-3],
&nbsp;              [-3,-3,-2]]
<strong>Output:</strong> -1
<strong>Explanation:</strong> It&#39;s not possible to get non-negative product in the path from (0, 0) to (2, 2), so return -1.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[<strong>1</strong>,-2,1],
&nbsp;              [<strong>1</strong>,<strong>-2</strong>,1],
&nbsp;              [3,<strong>-4</strong>,<strong>1</strong>]]
<strong>Output:</strong> 8
<strong>Explanation:</strong> Maximum non-negative product is in bold (1 * 1 * -2 * -4 * 1 = 8).
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> grid = [[<strong>1</strong>, 3],
&nbsp;              [<strong>0</strong>,<strong>-4</strong>]]
<strong>Output:</strong> 0
<strong>Explanation:</strong> Maximum non-negative product is in bold (1 * 0 * -4 = 0).
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> grid = [[ <strong>1</strong>, 4,4,0],
&nbsp;              [<strong>-2</strong>, 0,0,1],
&nbsp;              [ <strong>1</strong>,<strong>-1</strong>,<strong>1</strong>,<strong>1</strong>]]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Maximum non-negative product is in bold (1 * -2 * 1 * -1 * 1 * 1 = 2).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= rows, cols &lt;= 15</code></li>
	<li><code>-4 &lt;= grid[i][j] &lt;= 4</code></li>
</ul>
 instead-->
<p>给你一个大小为 <code>rows x cols</code> 的矩阵 <code>grid</code> 。最初，你位于左上角 <code>(0, 0)</code> ，每一步，你可以在矩阵中 <strong>向右</strong> 或 <strong>向下</strong> 移动。</p>

<p>在从左上角 <code>(0, 0)</code> 开始到右下角 <code>(rows - 1, cols - 1)</code> 结束的所有路径中，找出具有 <strong>最大非负积</strong> 的路径。路径的积是沿路径访问的单元格中所有整数的乘积。</p>

<p>返回 <strong>最大非负积 </strong>对<strong><em> </em><code>10<sup>9</sup>&nbsp;+ 7</code></strong> <strong>取余</strong> 的结果。如果最大积为负数，则返回<em> </em><code>-1</code> 。</p>

<p><strong>注意，</strong>取余是在得到最大积之后执行的。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>grid = [[-1,-2,-3],
&nbsp;            [-2,-3,-3],
&nbsp;            [-3,-3,-2]]
<strong>输出：</strong>-1
<strong>解释：</strong>从 (0, 0) 到 (2, 2) 的路径中无法得到非负积，所以返回 -1
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>grid = [[<strong>1</strong>,-2,1],
&nbsp;            [<strong>1</strong>,<strong>-2</strong>,1],
&nbsp;            [3,<strong>-4</strong>,<strong>1</strong>]]
<strong>输出：</strong>8
<strong>解释：</strong>最大非负积对应的路径已经用粗体标出 (1 * 1 * -2 * -4 * 1 = 8)
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>grid = [[<strong>1</strong>, 3],
&nbsp;            [<strong>0</strong>,<strong>-4</strong>]]
<strong>输出：</strong>0
<strong>解释：</strong>最大非负积对应的路径已经用粗体标出 (1 * 0 * -4 = 0)
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>grid = [[ <strong>1</strong>, 4,4,0],
&nbsp;            [<strong>-2</strong>, 0,0,1],
&nbsp;            [ <strong>1</strong>,<strong>-1</strong>,<strong>1</strong>,<strong>1</strong>]]
<strong>输出：</strong>2
<strong>解释：</strong>最大非负积对应的路径已经用粗体标出 (1 * -2 * 1 * -1 * 1 * 1 = 2)
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= rows, cols &lt;= 15</code></li>
	<li><code>-4 &lt;= grid[i][j] &lt;= 4</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
    public int maxProductPath(int[][] grid) {
        final int MOD = 1000000000 + 7;
        int m = grid.length, n = grid[0].length;
        long[][] maxgt = new long[m][n];
        long[][] minlt = new long[m][n];

        maxgt[0][0] = minlt[0][0] = grid[0][0];
        for (int i = 1; i < n; i++) {
            maxgt[0][i] = minlt[0][i] = maxgt[0][i - 1] * grid[0][i];
        }
        for (int i = 1; i < m; i++) {
            maxgt[i][0] = minlt[i][0] = maxgt[i - 1][0] * grid[i][0];
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (grid[i][j] >= 0) {
                    maxgt[i][j] = Math.max(maxgt[i][j - 1], maxgt[i - 1][j]) * grid[i][j];
                    minlt[i][j] = Math.min(minlt[i][j - 1], minlt[i - 1][j]) * grid[i][j];
                } else {
                    maxgt[i][j] = Math.min(minlt[i][j - 1], minlt[i - 1][j]) * grid[i][j];
                    minlt[i][j] = Math.max(maxgt[i][j - 1], maxgt[i - 1][j]) * grid[i][j];
                }
            }
        }
        if (maxgt[m - 1][n - 1] < 0) {
            return -1;
        } else {
            return (int) (maxgt[m - 1][n - 1] % MOD);
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-non-negative-product-in-a-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-non-negative-product-in-a-matrix/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-non-negative-product-in-a-matrix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-non-negative-product-in-a-matrix/)

[回到目录](../README.md)