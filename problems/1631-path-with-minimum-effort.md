# 1631. path-with-minimum-effort | 最小体力消耗路径

## Question description

<!--If you want to use the English description, use <p>You are a hiker preparing for an upcoming hike. You are given <code>heights</code>, a 2D array of size <code>rows x columns</code>, where <code>heights[row][col]</code> represents the height of cell <code>(row, col)</code>. You are situated in the top-left cell, <code>(0, 0)</code>, and you hope to travel to the bottom-right cell, <code>(rows-1, columns-1)</code> (i.e.,&nbsp;<strong>0-indexed</strong>). You can move <strong>up</strong>, <strong>down</strong>, <strong>left</strong>, or <strong>right</strong>, and you wish to find a route that requires the minimum <strong>effort</strong>.</p>

<p>A route&#39;s <strong>effort</strong> is the <strong>maximum absolute difference</strong><strong> </strong>in heights between two consecutive cells of the route.</p>

<p>Return <em>the minimum <strong>effort</strong> required to travel from the top-left cell to the bottom-right cell.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/10/04/ex1.png" style="width: 300px; height: 300px;" /></p>

<pre>
<strong>Input:</strong> heights = [[1,2,2],[3,8,2],[5,3,5]]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The route of [1,3,5,3,5] has a maximum absolute difference of 2 in consecutive cells.
This is better than the route of [1,2,2,2,5], where the maximum absolute difference is 3.
</pre>

<p><strong>Example 2:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/10/04/ex2.png" style="width: 300px; height: 300px;" /></p>

<pre>
<strong>Input:</strong> heights = [[1,2,3],[3,8,4],[5,3,5]]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The route of [1,2,3,4,5] has a maximum absolute difference of 1 in consecutive cells, which is better than route [1,3,5,3,5].
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/04/ex3.png" style="width: 300px; height: 300px;" />
<pre>
<strong>Input:</strong> heights = [[1,2,1,1,1],[1,2,1,2,1],[1,2,1,2,1],[1,2,1,2,1],[1,1,1,2,1]]
<strong>Output:</strong> 0
<strong>Explanation:</strong> This route does not require any effort.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>rows == heights.length</code></li>
	<li><code>columns == heights[i].length</code></li>
	<li><code>1 &lt;= rows, columns &lt;= 100</code></li>
	<li><code>1 &lt;= heights[i][j] &lt;= 10<sup>6</sup></code></li>
</ul> instead-->
<p>你准备参加一场远足活动。给你一个二维 <code>rows x columns</code> 的地图 <code>heights</code> ，其中 <code>heights[row][col]</code> 表示格子 <code>(row, col)</code> 的高度。一开始你在最左上角的格子 <code>(0, 0)</code> ，且你希望去最右下角的格子 <code>(rows-1, columns-1)</code> （注意下标从 <strong>0</strong> 开始编号）。你每次可以往 <strong>上</strong>，<strong>下</strong>，<strong>左</strong>，<strong>右</strong> 四个方向之一移动，你想要找到耗费 <strong>体力</strong> 最小的一条路径。</p>

<p>一条路径耗费的 <strong>体力值</strong> 是路径上相邻格子之间 <strong>高度差绝对值</strong> 的 <strong>最大值</strong> 决定的。</p>

<p>请你返回从左上角走到右下角的最小<strong> 体力消耗值</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/10/25/ex1.png" style="width: 300px; height: 300px;" /></p>

<pre>
<b>输入：</b>heights = [[1,2,2],[3,8,2],[5,3,5]]
<b>输出：</b>2
<b>解释：</b>路径 [1,3,5,3,5] 连续格子的差值绝对值最大为 2 。
这条路径比路径 [1,2,2,2,5] 更优，因为另一条路径差值最大值为 3 。
</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/10/25/ex2.png" style="width: 300px; height: 300px;" /></p>

<pre>
<b>输入：</b>heights = [[1,2,3],[3,8,4],[5,3,5]]
<b>输出：</b>1
<b>解释：</b>路径 [1,2,3,4,5] 的相邻格子差值绝对值最大为 1 ，比路径 [1,3,5,3,5] 更优。
</pre>

<p><strong>示例 3：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/10/25/ex3.png" style="width: 300px; height: 300px;" />
<pre>
<b>输入：</b>heights = [[1,2,1,1,1],[1,2,1,2,1],[1,2,1,2,1],[1,2,1,2,1],[1,1,1,2,1]]
<b>输出：</b>0
<b>解释：</b>上图所示路径不需要消耗任何体力。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>rows == heights.length</code></li>
	<li><code>columns == heights[i].length</code></li>
	<li><code>1 <= rows, columns <= 100</code></li>
	<li><code>1 <= heights[i][j] <= 10<sup>6</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 144 ms

```java
class Solution {
    int[][] dirs = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};

    public int minimumEffortPath(int[][] heights) {
        int m = heights.length;
        int n = heights[0].length;
        int left = 0, right = 999999, ans = 0;
        while (left <= right) {
            int mid = (left + right) / 2;
            Queue<int[]> queue = new LinkedList<int[]>();
            queue.offer(new int[]{0, 0});
            boolean[] seen = new boolean[m * n];
            seen[0] = true;
            while (!queue.isEmpty()) {
                int[] cell = queue.poll();
                int x = cell[0], y = cell[1];
                for (int i = 0; i < 4; ++i) {
                    int nx = x + dirs[i][0];
                    int ny = y + dirs[i][1];
                    if (nx >= 0 && nx < m && ny >= 0 && ny < n && !seen[nx * n + ny] && Math.abs(heights[x][y] - heights[nx][ny]) <= mid) {
                        queue.offer(new int[]{nx, ny});
                        seen[nx * n + ny] = true;
                    }
                }
            }
            if (seen[m * n - 1]) {
                ans = mid;
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/path-with-minimum-effort/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/path-with-minimum-effort/description/)

Solution: [LeetCode](https://leetcode.com/articles/path-with-minimum-effort/)  /  [LeetCode中国](https://leetcode-cn.com/articles/path-with-minimum-effort/)

[回到目录](../README.md)