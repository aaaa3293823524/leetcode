# 1411. number-of-ways-to-paint-n-3-grid | 给 N x 3 网格图涂色的方案数

## Question description

<!--If you want to use the English description, use <p>You have a <code>grid</code> of size <code>n x 3</code> and you want to paint each cell of the grid with exactly one of the three colors: <strong>Red</strong>, <strong>Yellow,</strong> or <strong>Green</strong> while making sure that no two adjacent cells have the same color (i.e., no two cells that share vertical or horizontal sides have the same color).</p>

<p>Given <code>n</code> the number of rows of the grid, return <em>the number of ways</em> you can paint this <code>grid</code>. As the answer may grow large, the answer <strong>must be</strong> computed modulo <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/03/26/e1.png" style="width: 400px; height: 257px;" />
<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> 12
<strong>Explanation:</strong> There are 12 possible way to paint the grid as shown.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 5000
<strong>Output:</strong> 30228214
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length</code></li>
	<li><code>1 &lt;= n &lt;= 5000</code></li>
</ul>
 instead-->
<p>你有一个 <code>n x 3</code>&nbsp;的网格图 <code>grid</code>&nbsp;，你需要用 <strong>红，黄，绿</strong>&nbsp;三种颜色之一给每一个格子上色，且确保相邻格子颜色不同（也就是有相同水平边或者垂直边的格子颜色不同）。</p>

<p>给你网格图的行数 <code>n</code>&nbsp;。</p>

<p>请你返回给&nbsp;<code>grid</code>&nbsp;涂色的方案数。由于答案可能会非常大，请你返回答案对&nbsp;<code>10^9 + 7</code>&nbsp;取余的结果。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>n = 1
<strong>输出：</strong>12
<strong>解释：</strong>总共有 12 种可行的方法：
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/04/12/e1.png" style="height: 289px; width: 450px;">
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>n = 2
<strong>输出：</strong>54
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>n = 3
<strong>输出：</strong>246
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>n = 7
<strong>输出：</strong>106494
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：</strong>n = 5000
<strong>输出：</strong>30228214
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == grid.length</code></li>
	<li><code>grid[i].length == 3</code></li>
	<li><code>1 &lt;= n &lt;= 5000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    static final int MOD = 1000000007;

    public int numOfWays(int n) {
        long fi0 = 6, fi1 = 6;
        for (int i = 2; i <= n; ++i) {
            long newFi0 = (2 * fi0 + 2 * fi1) % MOD;
            long newFi1 = (2 * fi0 + 3 * fi1) % MOD;
            fi0 = newFi0;
            fi1 = newFi1;
        }
        return (int) ((fi0 + fi1) % MOD);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-ways-to-paint-n-3-grid/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-ways-to-paint-n-3-grid/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-ways-to-paint-n-3-grid/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-ways-to-paint-n-3-grid/)

[回到目录](../README.md)