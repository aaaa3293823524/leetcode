# 2017. grid-game | 网格游戏

## Question description

<!--If you want to use the English description, use <p>You are given a <strong>0-indexed</strong> 2D array <code>grid</code> of size <code>2 x n</code>, where <code>grid[r][c]</code> represents the number of points at position <code>(r, c)</code> on the matrix. Two robots are playing a game on this matrix.</p>

<p>Both robots initially start at <code>(0, 0)</code> and want to reach <code>(1, n-1)</code>. Each robot may only move to the <strong>right</strong> (<code>(r, c)</code> to <code>(r, c + 1)</code>) or <strong>down </strong>(<code>(r, c)</code> to <code>(r + 1, c)</code>).</p>

<p>At the start of the game, the <strong>first</strong> robot moves from <code>(0, 0)</code> to <code>(1, n-1)</code>, collecting all the points from the cells on its path. For all cells <code>(r, c)</code> traversed on the path, <code>grid[r][c]</code> is set to <code>0</code>. Then, the <strong>second</strong> robot moves from <code>(0, 0)</code> to <code>(1, n-1)</code>, collecting the points on its path. Note that their paths may intersect with one another.</p>

<p>The <strong>first</strong> robot wants to <strong>minimize</strong> the number of points collected by the <strong>second</strong> robot. In contrast, the <strong>second </strong>robot wants to <strong>maximize</strong> the number of points it collects. If both robots play <strong>optimally</strong>, return <em>the <b>number of points</b> collected by the <strong>second</strong> robot.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/09/08/a1.png" style="width: 388px; height: 103px;" />
<pre>
<strong>Input:</strong> grid = [[2,5,4],[1,5,1]]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The optimal path taken by the first robot is shown in red, and the optimal path taken by the second robot is shown in blue.
The cells visited by the first robot are set to 0.
The second robot will collect 0 + 0 + 4 + 0 = 4 points.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/09/08/a2.png" style="width: 384px; height: 105px;" />
<pre>
<strong>Input:</strong> grid = [[3,3,1],[8,5,2]]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The optimal path taken by the first robot is shown in red, and the optimal path taken by the second robot is shown in blue.
The cells visited by the first robot are set to 0.
The second robot will collect 0 + 3 + 1 + 0 = 4 points.
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/09/08/a3.png" style="width: 493px; height: 103px;" />
<pre>
<strong>Input:</strong> grid = [[1,3,1,15],[1,3,3,1]]
<strong>Output:</strong> 7
<strong>Explanation: </strong>The optimal path taken by the first robot is shown in red, and the optimal path taken by the second robot is shown in blue.
The cells visited by the first robot are set to 0.
The second robot will collect 0 + 1 + 3 + 3 + 0 = 7 points.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>grid.length == 2</code></li>
	<li><code>n == grid[r].length</code></li>
	<li><code>1 &lt;= n &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= grid[r][c] &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>给你一个下标从 <strong>0</strong> 开始的二维数组 <code>grid</code> ，数组大小为 <code>2 x n</code> ，其中 <code>grid[r][c]</code> 表示矩阵中 <code>(r, c)</code> 位置上的点数。现在有两个机器人正在矩阵上参与一场游戏。</p>

<p>两个机器人初始位置都是 <code>(0, 0)</code> ，目标位置是 <code>(1, n-1)</code> 。每个机器人只会 <strong>向右</strong> (<code>(r, c)</code> 到 <code>(r, c + 1)</code>) 或 <strong>向下 </strong>(<code>(r, c)</code> 到 <code>(r + 1, c)</code>) 。</p>

<p>游戏开始，<strong>第一个</strong> 机器人从 <code>(0, 0)</code> 移动到 <code>(1, n-1)</code> ，并收集路径上单元格的全部点数。对于路径上所有单元格 <code>(r, c)</code> ，途经后 <code>grid[r][c]</code> 会重置为 <code>0</code> 。然后，<strong>第二个</strong> 机器人从 <code>(0, 0)</code> 移动到 <code>(1, n-1)</code> ，同样收集路径上单元的全部点数。注意，它们的路径可能会存在相交的部分。</p>

<p><strong>第一个</strong> 机器人想要打击竞争对手，使 <strong>第二个</strong> 机器人收集到的点数 <strong>最小化</strong> 。与此相对，<strong>第二个</strong> 机器人想要 <strong>最大化</strong> 自己收集到的点数。两个机器人都发挥出自己的 <strong>最佳水平</strong>&nbsp;的前提下，返回 <strong>第二个</strong> 机器人收集到的 <strong>点数</strong> <em>。</em></p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/09/08/a1.png" style="width: 388px; height: 103px;" /></p>

<pre>
<strong>输入：</strong>grid = [[2,5,4],[1,5,1]]
<strong>输出：</strong>4
<strong>解释：</strong>第一个机器人的最佳路径如红色所示，第二个机器人的最佳路径如蓝色所示。
第一个机器人访问过的单元格将会重置为 0 。
第二个机器人将会收集到 0 + 0 + 4 + 0 = 4 个点。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/09/08/a2.png" style="width: 384px; height: 105px;" />
<pre>
<strong>输入：</strong>grid = [[3,3,1],[8,5,2]]
<strong>输出：</strong>4
<strong>解释：</strong>第一个机器人的最佳路径如红色所示，第二个机器人的最佳路径如蓝色所示。 
第一个机器人访问过的单元格将会重置为 0 。
第二个机器人将会收集到 0 + 3 + 1 + 0 = 4 个点。
</pre>

<p><strong>示例 3：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/09/08/a3.png" style="width: 493px; height: 103px;" />
<pre>
<strong>输入：</strong>grid = [[1,3,1,15],[1,3,3,1]]
<strong>输出：</strong>7
<strong>解释：</strong>第一个机器人的最佳路径如红色所示，第二个机器人的最佳路径如蓝色所示。
第一个机器人访问过的单元格将会重置为 0 。
第二个机器人将会收集到 0 + 1 + 3 + 3 + 0 = 7 个点。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>grid.length == 2</code></li>
	<li><code>n == grid[r].length</code></li>
	<li><code>1 &lt;= n &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>1 &lt;= grid[r][c] &lt;= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public long gridGame(int[][] grid) {
        int l = grid[0].length;
        long[] one_qian = new long[l];
        long[] two_hou = new long[l];

        one_qian[0] = grid[0][0];
        for(int i=1;i<l;i++){
            one_qian[i] = one_qian[i-1] + grid[0][i];
        }

        two_hou[l-1] = grid[1][l-1];
        for(int i=l-2;i>=0;i--){
            two_hou[i] = two_hou[i+1] + grid[1][i];
        }
        
        long min =one_qian[l-1]+two_hou[l-1];
        for(int i=0;i<l;i++){//枚举第1个机器人下去的地方
                min=(Math.min(min,Math.max(two_hou[0]-two_hou[i],one_qian[l-1]-one_qian[i])));
               // System.out.println(i+" "+j+" "+max);
        }
            //System.out.println(max);



       
        
        //for(int i=0)
        return min;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/grid-game/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/grid-game/description/)

Solution: [LeetCode](https://leetcode.com/articles/grid-game/)  /  [LeetCode中国](https://leetcode-cn.com/articles/grid-game/)

[回到目录](../README.md)