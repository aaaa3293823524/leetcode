# 1039. minimum-score-triangulation-of-polygon | 多边形三角剖分的最低得分

## Question description

<!--If you want to use the English description, use <p>You have a convex <code>n</code>-sided polygon where each vertex has an integer value. You are given an integer array <code>values</code> where <code>values[i]</code> is the value of the <code>i<sup>th</sup></code> vertex (i.e., <strong>clockwise order</strong>).</p>

<p>You will <strong>triangulate</strong> the polygon into <code>n - 2</code> triangles. For each triangle, the value of that triangle is the product of the values of its vertices, and the total score of the triangulation is the sum of these values over all <code>n - 2</code> triangles in the triangulation.</p>

<p>Return <em>the smallest possible total score that you can achieve with some triangulation of the polygon</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/25/shape1.jpg" style="width: 201px; height: 133px;" />
<pre>
<strong>Input:</strong> values = [1,2,3]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The polygon is already triangulated, and the score of the only triangle is 6.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/25/shape2.jpg" style="width: 446px; height: 163px;" />
<pre>
<strong>Input:</strong> values = [3,7,4,5]
<strong>Output:</strong> 144
<strong>Explanation:</strong> There are two triangulations, with possible scores: 3*7*5 + 4*5*7 = 245, or 3*4*5 + 3*4*7 = 144.
The minimum score is 144.
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/02/25/shape3.jpg" style="width: 207px; height: 163px;" />
<pre>
<strong>Input:</strong> values = [1,3,1,4,1,5]
<strong>Output:</strong> 13
<strong>Explanation:</strong> The minimum score triangulation has score 1*1*3 + 1*1*4 + 1*1*5 + 1*1*1 = 13.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == values.length</code></li>
	<li><code>3 &lt;= n &lt;= 50</code></li>
	<li><code>1 &lt;= values[i] &lt;= 100</code></li>
</ul>
 instead-->
<p>给定&nbsp;<code>N</code>，想象一个凸&nbsp;<code>N</code>&nbsp;边多边形，其顶点按顺时针顺序依次标记为&nbsp;<code>A[0], A[i], ..., A[N-1]</code>。</p>

<p>假设您将多边形剖分为 <code>N-2</code> 个三角形。对于每个三角形，该三角形的值是顶点标记的<strong>乘积</strong>，三角剖分的分数是进行三角剖分后所有 <code>N-2</code> 个三角形的值之和。</p>

<p>返回多边形进行三角剖分后可以得到的最低分。<br>
&nbsp;</p>

<ol>
</ol>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>[1,2,3]
<strong>输出：</strong>6
<strong>解释：</strong>多边形已经三角化，唯一三角形的分数为 6。
</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/05/03/minimum-score-triangulation-of-polygon-1.png" style="height: 150px; width: 253px;"></p>

<pre><strong>输入：</strong>[3,7,4,5]
<strong>输出：</strong>144
<strong>解释：</strong>有两种三角剖分，可能得分分别为：3*7*5 + 4*5*7 = 245，或 3*4*5 + 3*4*7 = 144。最低分数为 144。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>[1,3,1,4,1,5]
<strong>输出：</strong>13
<strong>解释：</strong>最低分数三角剖分的得分情况为 1*1*3 + 1*1*4 + 1*1*5 + 1*1*1 = 13。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>3 &lt;= A.length &lt;= 50</code></li>
	<li><code>1 &lt;= A[i] &lt;= 100</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int minScoreTriangulation(int[] values) {
        int n = values.length;
        int[][] dp = new int[n][n];
        for (int i = 0; i < n; i++) Arrays.fill(dp[i], 0xffffff);
        for (int len = 1; len <= n; len++) { //枚举区间长度
            for (int le = 0; le + (len - 1) < n; le++) { //枚举区间左端点
                int ri = le + (len - 1); //计算区间右端点
                if (len == 1 || len == 2) { //区间长度为1或2特值为0
                    dp[le][ri] = 0;
                } else {
                    for (int mid = le + 1; mid < ri; mid++) { //枚举该区间任意一个包含左端点、右端点为顶点的三角形
                        dp[le][ri] = Math.min(dp[le][ri], 
                                              dp[le][mid] + values[le] * values[mid] * values[ri] + dp[mid][ri]);
                    }
                }
            }
        }
        return dp[0][n - 1];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-score-triangulation-of-polygon/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-score-triangulation-of-polygon/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-score-triangulation-of-polygon/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-score-triangulation-of-polygon/)

[回到目录](../README.md)