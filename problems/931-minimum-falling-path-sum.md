# 931. minimum-falling-path-sum | 下降路径最小和

## Question description

<!--If you want to use the English description, use <p>Given an <code>n x n</code> array of integers <code>matrix</code>, return <em>the <strong>minimum sum</strong> of any <strong>falling path</strong> through</em> <code>matrix</code>.</p>

<p>A <strong>falling path</strong> starts at any element in the first row and chooses the element in the next row that is either directly below or diagonally left/right. Specifically, the next element from position <code>(row, col)</code> will be <code>(row + 1, col - 1)</code>, <code>(row + 1, col)</code>, or <code>(row + 1, col + 1)</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/11/03/failing1-grid.jpg" style="width: 499px; height: 500px;" />
<pre>
<strong>Input:</strong> matrix = [[2,1,3],[6,5,4],[7,8,9]]
<strong>Output:</strong> 13
<strong>Explanation:</strong> There are two falling paths with a minimum sum as shown.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/11/03/failing2-grid.jpg" style="width: 164px; height: 365px;" />
<pre>
<strong>Input:</strong> matrix = [[-19,57],[-40,-5]]
<strong>Output:</strong> -59
<strong>Explanation:</strong> The falling path with a minimum sum is shown.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == matrix.length == matrix[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>-100 &lt;= matrix[i][j] &lt;= 100</code></li>
</ul>
 instead-->
<p>给你一个 <code>n x n</code> 的<strong> 方形 </strong>整数数组&nbsp;<code>matrix</code> ，请你找出并返回通过 <code>matrix</code> 的<strong>下降路径</strong><em> </em>的<strong> </strong><strong>最小和</strong> 。</p>

<p><strong>下降路径</strong> 可以从第一行中的任何元素开始，并从每一行中选择一个元素。在下一行选择的元素和当前行所选元素最多相隔一列（即位于正下方或者沿对角线向左或者向右的第一个元素）。具体来说，位置 <code>(row, col)</code> 的下一个元素应当是 <code>(row + 1, col - 1)</code>、<code>(row + 1, col)</code> 或者 <code>(row + 1, col + 1)</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>matrix = [[2,1,3],[6,5,4],[7,8,9]]
<strong>输出：</strong>13
<strong>解释：</strong>下面是两条和最小的下降路径，用加粗+斜体标注：
[[2,<em><strong>1</strong></em>,3],      [[2,<em><strong>1</strong></em>,3],
 [6,<em><strong>5</strong></em>,4],       [6,5,<em><strong>4</strong></em>],
 [<em><strong>7</strong></em>,8,9]]       [7,<em><strong>8</strong></em>,9]]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>matrix = [[-19,57],[-40,-5]]
<strong>输出：</strong>-59
<strong>解释：</strong>下面是一条和最小的下降路径，用加粗+斜体标注：
[[<em><strong>-19</strong></em>,57],
 [<em><strong>-40</strong></em>,-5]]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>matrix = [[-48]]
<strong>输出：</strong>-48
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>-100 &lt;= matrix[i][j] &lt;= 100</code></li>
</ul>


## Note

动态规划



从倒数第2行依次修改数组  直到第1行 取最小值


## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public int minFallingPathSum(int[][] A) {
        int N = A.length;
        for (int r = N-2; r >= 0; --r) {
            for (int c = 0; c < N; ++c) {
                // best = min(A[r+1][c-1], A[r+1][c], A[r+1][c+1])
                int best = A[r+1][c];
                if (c > 0)
                    best = Math.min(best, A[r+1][c-1]);
                if (c+1 < N)
                    best = Math.min(best, A[r+1][c+1]);
                A[r][c] += best;
            }
        }

        int ans = Integer.MAX_VALUE;
        for (int x: A[0])
            ans = Math.min(ans, x);
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-falling-path-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-falling-path-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-falling-path-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-falling-path-sum/)

[回到目录](../README.md)