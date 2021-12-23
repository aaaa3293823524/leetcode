# 861. score-after-flipping-matrix | 翻转矩阵后的得分

## Question description

<!--If you want to use the English description, use <p>You are given an <code>m x n</code> binary matrix <code>grid</code>.</p>

<p>A <strong>move</strong> consists of choosing any row or column and toggling each value in that row or column (i.e., changing all <code>0</code>&#39;s to <code>1</code>&#39;s, and all <code>1</code>&#39;s to <code>0</code>&#39;s).</p>

<p>Every row of the matrix is interpreted as a binary number, and the <strong>score</strong> of the matrix is the sum of these numbers.</p>

<p>Return <em>the highest possible <strong>score</strong> after making any number of <strong>moves</strong> (including zero moves)</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/07/23/lc-toogle1.jpg" style="width: 500px; height: 299px;" />
<pre>
<strong>Input:</strong> grid = [[0,0,1,1],[1,0,1,0],[1,1,0,0]]
<strong>Output:</strong> 39
<strong>Explanation:</strong> 0b1111 + 0b1001 + 0b1111 = 15 + 9 + 15 = 39
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[0]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 20</code></li>
	<li><code>grid[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>
 instead-->
<p>有一个二维矩阵&nbsp;<code>A</code> 其中每个元素的值为&nbsp;<code>0</code>&nbsp;或&nbsp;<code>1</code>&nbsp;。</p>

<p>移动是指选择任一行或列，并转换该行或列中的每一个值：将所有 <code>0</code> 都更改为 <code>1</code>，将所有 <code>1</code> 都更改为 <code>0</code>。</p>

<p>在做出任意次数的移动后，将该矩阵的每一行都按照二进制数来解释，矩阵的得分就是这些数字的总和。</p>

<p>返回尽可能高的分数。</p>

<p>&nbsp;</p>

<ol>
</ol>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[[0,0,1,1],[1,0,1,0],[1,1,0,0]]
<strong>输出：</strong>39
<strong>解释：
</strong>转换为 [[1,1,1,1],[1,0,0,1],[1,1,1,1]]
0b1111 + 0b1001 + 0b1111 = 15 + 9 + 15 = 39</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= A.length &lt;= 20</code></li>
	<li><code>1 &lt;= A[0].length &lt;= 20</code></li>
	<li><code>A[i][j]</code>&nbsp;是&nbsp;<code>0</code> 或&nbsp;<code>1</code></li>
</ol>


## Note

贪心   先行反转使最高位为1   之后考虑列使1个数最多（计算每列0和1的最大值）


## Solution

Language: **cpp**  /  Runtime: 4 ms

```cpp
class Solution {
public:
    int matrixScore(vector<vector<int>>& A) {
        int m = A.size(), n = A[0].size();
        int ret = m * (1 << (n - 1));

        for (int j = 1; j < n; j++) {
            int nOnes = 0;
            for (int i = 0; i < m; i++) {
                if (A[i][0] == 1) {
                    nOnes += A[i][j];
                } else {
                    nOnes += (1 - A[i][j]); // 如果这一行进行了行反转，则该元素的实际取值为 1 - A[i][j]
                }
            }
            int k = max(nOnes, m - nOnes);
            ret += k * (1 << (n - j - 1));
        }
        return ret;
    }
};

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/score-after-flipping-matrix/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/score-after-flipping-matrix/description/)

Solution: [LeetCode](https://leetcode.com/articles/score-after-flipping-matrix/)  /  [LeetCode中国](https://leetcode-cn.com/articles/score-after-flipping-matrix/)

[回到目录](../README.md)