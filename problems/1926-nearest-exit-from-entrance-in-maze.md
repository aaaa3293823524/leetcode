# 1926. nearest-exit-from-entrance-in-maze | 迷宫中离入口最近的出口

## Question description

<!--If you want to use the English description, use <p>You are given an <code>m x n</code> matrix <code>maze</code> (<strong>0-indexed</strong>) with empty cells (represented as <code>&#39;.&#39;</code>) and walls (represented as <code>&#39;+&#39;</code>). You are also given the <code>entrance</code> of the maze, where <code>entrance = [entrance<sub>row</sub>, entrance<sub>col</sub>]</code> denotes the row and column of the cell you are initially standing at.</p>

<p>In one step, you can move one cell <strong>up</strong>, <strong>down</strong>, <strong>left</strong>, or <strong>right</strong>. You cannot step into a cell with a wall, and you cannot step outside the maze. Your goal is to find the <strong>nearest exit</strong> from the <code>entrance</code>. An <strong>exit</strong> is defined as an <strong>empty cell</strong> that is at the <strong>border</strong> of the <code>maze</code>. The <code>entrance</code> <strong>does not count</strong> as an exit.</p>

<p>Return <em>the <strong>number of steps</strong> in the shortest path from the </em><code>entrance</code><em> to the nearest exit, or </em><code>-1</code><em> if no such path exists</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/04/nearest1-grid.jpg" style="width: 333px; height: 253px;" />
<pre>
<strong>Input:</strong> maze = [[&quot;+&quot;,&quot;+&quot;,&quot;.&quot;,&quot;+&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;+&quot;],[&quot;+&quot;,&quot;+&quot;,&quot;+&quot;,&quot;.&quot;]], entrance = [1,2]
<strong>Output:</strong> 1
<strong>Explanation:</strong> There are 3 exits in this maze at [1,0], [0,2], and [2,3].
Initially, you are at the entrance cell [1,2].
- You can reach [1,0] by moving 2 steps left.
- You can reach [0,2] by moving 1 step up.
It is impossible to reach [2,3] from the entrance.
Thus, the nearest exit is [0,2], which is 1 step away.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/04/nearesr2-grid.jpg" style="width: 253px; height: 253px;" />
<pre>
<strong>Input:</strong> maze = [[&quot;+&quot;,&quot;+&quot;,&quot;+&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;],[&quot;+&quot;,&quot;+&quot;,&quot;+&quot;]], entrance = [1,0]
<strong>Output:</strong> 2
<strong>Explanation:</strong> There is 1 exit in this maze at [1,2].
[1,0] does not count as an exit since it is the entrance cell.
Initially, you are at the entrance cell [1,0].
- You can reach [1,2] by moving 2 steps right.
Thus, the nearest exit is [1,2], which is 2 steps away.
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/04/nearest3-grid.jpg" style="width: 173px; height: 93px;" />
<pre>
<strong>Input:</strong> maze = [[&quot;.&quot;,&quot;+&quot;]], entrance = [0,0]
<strong>Output:</strong> -1
<strong>Explanation:</strong> There are no exits in this maze.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>maze.length == m</code></li>
	<li><code>maze[i].length == n</code></li>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li><code>maze[i][j]</code> is either <code>&#39;.&#39;</code> or <code>&#39;+&#39;</code>.</li>
	<li><code>entrance.length == 2</code></li>
	<li><code>0 &lt;= entrance<sub>row</sub> &lt; m</code></li>
	<li><code>0 &lt;= entrance<sub>col</sub> &lt; n</code></li>
	<li><code>entrance</code> will always be an empty cell.</li>
</ul>
 instead-->
<p>给你一个 <code>m x n</code> 的迷宫矩阵 <code>maze</code> （<strong>下标从 0 开始</strong>），矩阵中有空格子（用 <code>'.'</code> 表示）和墙（用 <code>'+'</code> 表示）。同时给你迷宫的入口 <code>entrance</code> ，用 <code>entrance = [entrance<sub>row</sub>, entrance<sub>col</sub>]</code> 表示你一开始所在格子的行和列。</p>

<p>每一步操作，你可以往 <strong>上</strong>，<strong>下</strong>，<strong>左</strong> 或者 <strong>右</strong> 移动一个格子。你不能进入墙所在的格子，你也不能离开迷宫。你的目标是找到离 <code>entrance</code> <strong>最近</strong> 的出口。<strong>出口</strong> 的含义是 <code>maze</code> <strong>边界</strong> 上的 <strong>空格子</strong>。<code>entrance</code> 格子 <strong>不算</strong> 出口。</p>

<p>请你返回从 <code>entrance</code> 到最近出口的最短路径的 <strong>步数</strong> ，如果不存在这样的路径，请你返回 <code>-1</code> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/04/nearest1-grid.jpg" style="width: 333px; height: 253px;">
<pre><b>输入：</b>maze = [["+","+",".","+"],[".",".",".","+"],["+","+","+","."]], entrance = [1,2]
<b>输出：</b>1
<b>解释：</b>总共有 3 个出口，分别位于 (1,0)，(0,2) 和 (2,3) 。
一开始，你在入口格子 (1,2) 处。
- 你可以往左移动 2 步到达 (1,0) 。
- 你可以往上移动 1 步到达 (0,2) 。
从入口处没法到达 (2,3) 。
所以，最近的出口是 (0,2) ，距离为 1 步。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/04/nearesr2-grid.jpg" style="width: 253px; height: 253px;">
<pre><b>输入：</b>maze = [["+","+","+"],[".",".","."],["+","+","+"]], entrance = [1,0]
<b>输出：</b>2
<b>解释：</b>迷宫中只有 1 个出口，在 (1,2) 处。
(1,0) 不算出口，因为它是入口格子。
初始时，你在入口与格子 (1,0) 处。
- 你可以往右移动 2 步到达 (1,2) 处。
所以，最近的出口为 (1,2) ，距离为 2 步。
</pre>

<p><strong>示例 3：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/04/nearest3-grid.jpg" style="width: 173px; height: 93px;">
<pre><b>输入：</b>maze = [[".","+"]], entrance = [0,0]
<b>输出：</b>-1
<b>解释：</b>这个迷宫中没有出口。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>maze.length == m</code></li>
	<li><code>maze[i].length == n</code></li>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li><code>maze[i][j]</code> 要么是 <code>'.'</code> ，要么是 <code>'+'</code> 。</li>
	<li><code>entrance.length == 2</code></li>
	<li><code>0 &lt;= entrance<sub>row</sub> &lt; m</code></li>
	<li><code>0 &lt;= entrance<sub>col</sub> &lt; n</code></li>
	<li><code>entrance</code> 一定是空格子。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public int nearestExit(char[][] maze, int[] entrance) {
        //
        int res = 0;
        int[][] locations =
                new int[][]{{1, 0}, {0, 1}, {-1, 0}, {0, -1}};  //4个方向
        Queue<int[]> queue = new LinkedList<>();
        int x = entrance[0],y = entrance[1];
        queue.add(entrance);
        maze[x][y] = '+';
        while(!queue.isEmpty()) {
            int size = queue.size();
            res += 1;
            for(int t = 0; t < size; t++) {
                int[] cur = queue.poll();
                for (int i = 0; i < locations.length; i++) {
                    int dx = cur[0] + locations[i][0];
                    int dy = cur[1] + locations[i][1];
                    if (dx >= 0 && dx < maze.length && dy >= 0
                            && dy < maze[0].length && maze[dx][dy] == '.'){
                        if (dx == 0 || dx == maze.length-1
                                || dy == 0 || dy == maze[0].length-1) {
                            return res;
                        }
                        maze[dx][dy] = '+';
                        queue.add(new int[]{dx,dy});
                    }
                }
            }
        }
        return -1;
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/nearest-exit-from-entrance-in-maze/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/nearest-exit-from-entrance-in-maze/description/)

Solution: [LeetCode](https://leetcode.com/articles/nearest-exit-from-entrance-in-maze/)  /  [LeetCode中国](https://leetcode-cn.com/articles/nearest-exit-from-entrance-in-maze/)

[回到目录](../README.md)