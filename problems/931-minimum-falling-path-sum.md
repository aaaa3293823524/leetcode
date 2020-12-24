# 931. minimum-falling-path-sum | 下降路径最小和

## Question description

<!--If you want to use the English description, use <p>Given a <strong>square</strong> array of integers <code>A</code>, we want the <strong>minimum</strong> sum of a <em>falling path</em> through <code>A</code>.</p>

<p>A falling path starts at any element in the first row, and chooses one element from each row.&nbsp; The next row&#39;s choice must be in a column that is different from the previous row&#39;s column by at most one.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[[1,2,3],[4,5,6],[7,8,9]]</span>
<strong>Output: </strong><span id="example-output-1">12</span>
<strong>Explanation: </strong>
The possible falling paths are:
</pre>

<ul>
	<li><code>[1,4,7], [1,4,8], [1,5,7], [1,5,8], [1,5,9]</code></li>
	<li><code>[2,4,7], [2,4,8], [2,5,7], [2,5,8], [2,5,9], [2,6,8], [2,6,9]</code></li>
	<li><code>[3,5,7], [3,5,8], [3,5,9], [3,6,8], [3,6,9]</code></li>
</ul>

<p>The falling path with the smallest sum is <code>[1,4,7]</code>, so the answer is <code>12</code>.</p>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= A.length == A[0].length &lt;= 100</code></li>
	<li><code>-100 &lt;= A[i][j] &lt;= 100</code></li>
</ul>
 instead-->
<p>给定一个<strong>方形</strong>整数数组&nbsp;<code>A</code>，我们想要得到通过 <code>A</code> 的<em>下降路径</em>的<strong>最小</strong>和。</p>

<p>下降路径可以从第一行中的任何元素开始，并从每一行中选择一个元素。在下一行选择的元素和当前行所选元素最多相隔一列。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[[1,2,3],[4,5,6],[7,8,9]]
<strong>输出：</strong>12
<strong>解释：</strong>
可能的下降路径有：
</pre>

<ul>
	<li><code>[1,4,7], [1,4,8], [1,5,7], [1,5,8], [1,5,9]</code></li>
	<li><code>[2,4,7], [2,4,8], [2,5,7], [2,5,8], [2,5,9], [2,6,8], [2,6,9]</code></li>
	<li><code>[3,5,7], [3,5,8], [3,5,9], [3,6,8], [3,6,9]</code></li>
</ul>

<p>和最小的下降路径是&nbsp;<code>[1,4,7]</code>，所以答案是&nbsp;<code>12</code>。</p>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length == A[0].length &lt;= 100</code></li>
	<li><code>-100 &lt;= A[i][j] &lt;= 100</code></li>
</ol>


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