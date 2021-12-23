# 913. cat-and-mouse | 猫和老鼠

## Question description

<!--If you want to use the English description, use <p>A game on an <strong>undirected</strong> graph is played by two players, Mouse and Cat, who alternate turns.</p>

<p>The graph is given as follows: <code>graph[a]</code> is a list of all nodes <code>b</code> such that <code>ab</code> is an edge of the graph.</p>

<p>The mouse starts at node <code>1</code> and goes first, the cat starts at node <code>2</code> and goes second, and there is a hole at node <code>0</code>.</p>

<p>During each player&#39;s turn, they <strong>must</strong> travel along one&nbsp;edge of the graph that meets where they are.&nbsp; For example, if the Mouse is at node 1, it <strong>must</strong> travel to any node in <code>graph[1]</code>.</p>

<p>Additionally, it is not allowed for the Cat to travel to the Hole (node 0.)</p>

<p>Then, the game can end in three&nbsp;ways:</p>

<ul>
	<li>If ever the Cat occupies the same node as the Mouse, the Cat wins.</li>
	<li>If ever the Mouse reaches the Hole, the Mouse wins.</li>
	<li>If ever a position is repeated (i.e., the players are in the same position as a previous turn, and&nbsp;it is the same player&#39;s turn to move), the game is a draw.</li>
</ul>

<p>Given a <code>graph</code>, and assuming both players play optimally, return</p>

<ul>
	<li><code>1</code>&nbsp;if the mouse wins the game,</li>
	<li><code>2</code>&nbsp;if the cat wins the game, or</li>
	<li><code>0</code>&nbsp;if the game is a draw.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/17/cat1.jpg" style="width: 300px; height: 300px;" />
<pre>
<strong>Input:</strong> graph = [[2,5],[3],[0,4,5],[1,4,5],[2,3],[0,2,3]]
<strong>Output:</strong> 0
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/17/cat2.jpg" style="width: 200px; height: 200px;" />
<pre>
<strong>Input:</strong> graph = [[1,3],[0],[3],[0,2]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= graph.length &lt;= 50</code></li>
	<li><code>1&nbsp;&lt;= graph[i].length &lt; graph.length</code></li>
	<li><code>0 &lt;= graph[i][j] &lt; graph.length</code></li>
	<li><code>graph[i][j] != i</code></li>
	<li><code>graph[i]</code> is unique.</li>
	<li>The mouse and the cat can always move.&nbsp;</li>
</ul>
 instead-->
<p>两位玩家分别扮演猫和老鼠，在一张 <strong>无向</strong> 图上进行游戏，两人轮流行动。</p>

<p>图的形式是：<code>graph[a]</code> 是一个列表，由满足&nbsp;<code>ab</code> 是图中的一条边的所有节点 <code>b</code> 组成。</p>

<p>老鼠从节点 <code>1</code> 开始，第一个出发；猫从节点 <code>2</code> 开始，第二个出发。在节点 <code>0</code> 处有一个洞。</p>

<p>在每个玩家的行动中，他们 <strong>必须</strong> 沿着图中与所在当前位置连通的一条边移动。例如，如果老鼠在节点 <code>1</code> ，那么它必须移动到 <code>graph[1]</code> 中的任一节点。</p>

<p>此外，猫无法移动到洞中（节点 <code>0</code>）。</p>

<p>然后，游戏在出现以下三种情形之一时结束：</p>

<ul>
	<li>如果猫和老鼠出现在同一个节点，猫获胜。</li>
	<li>如果老鼠到达洞中，老鼠获胜。</li>
	<li>如果某一位置重复出现（即，玩家的位置和移动顺序都与上一次行动相同），游戏平局。</li>
</ul>

<p>给你一张图 <code>graph</code> ，并假设两位玩家都都以最佳状态参与游戏：</p>

<ul>
	<li>如果老鼠获胜，则返回&nbsp;<code>1</code>；</li>
	<li>如果猫获胜，则返回 <code>2</code>；</li>
	<li>如果平局，则返回 <code>0</code> 。</li>
</ul>
&nbsp;

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/17/cat1.jpg" style="width: 300px; height: 300px;" />
<pre>
<strong>输入：</strong>graph = [[2,5],[3],[0,4,5],[1,4,5],[2,3],[0,2,3]]
<strong>输出：</strong>0
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/17/cat2.jpg" style="width: 200px; height: 200px;" />
<pre>
<strong>输入：</strong>graph = [[1,3],[0],[3],[0,2]]
<strong>输出：</strong>1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>3 &lt;= graph.length &lt;= 50</code></li>
	<li><code>1&nbsp;&lt;= graph[i].length &lt; graph.length</code></li>
	<li><code>0 &lt;= graph[i][j] &lt; graph.length</code></li>
	<li><code>graph[i][j] != i</code></li>
	<li><code>graph[i]</code> 互不相同</li>
	<li>猫和老鼠在游戏中总是移动</li>
</ul>




## Solution

Language: **java**  /  Runtime: 12 ms

```java
class Solution {
    int n;
    public int catMouseGame(int[][] graph) {
        n = graph.length;
        int[][][] dp = new int[2 * n][n][n];
        int ans = helper(graph , 0 , 1 , 2 , dp);
        return ans == 3 ? 0 : ans;
    }
    public int helper(int[][] graph , int t , int x , int y , int[][][] dp){
        if(t == 2 * n) return 3;
        if(x == y){
            dp[t][x][y] = 2;
            return 2;
        }
        if(x == 0){
            dp[t][x][y] = 1;
            return 1;
        }
        if(dp[t][x][y] != 0){
            return dp[t][x][y];
        }
        if(t % 2 == 0){
            boolean catWin = true;
            for(int i = 0 ; i < graph[x].length ; i++){
                int nx = graph[x][i];
                int next = helper(graph, t + 1, nx, y, dp);
                if (next == 1){
                    dp[t][x][y] = 1;
                    return 1;
                }else if(next != 2){
                    catWin = false;
                }                  
            }
            if(catWin){
                dp[t][x][y] = 2;
                return 2;
            }else{
                dp[t][x][y] = 3;
                return 3;
            }
        }else{
            boolean mouseWin = true;
            for (int i = 0 ; i < graph[y].length ; i++){
                int ny = graph[y][i];
                if (ny == 0) continue;
                int next = helper(graph, t + 1, x, ny, dp);
                if (next == 2){
                    dp[t][x][y] = 2;
                    return 2;
                }else if (next != 1) {
                    mouseWin = false;
                }
            }
            if (mouseWin) {
                dp[t][x][y] = 1;
                return 1;
            }else{
                dp[t][x][y] = 3;
                return 3;
            }
        }
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/cat-and-mouse/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/cat-and-mouse/description/)

Solution: [LeetCode](https://leetcode.com/articles/cat-and-mouse/)  /  [LeetCode中国](https://leetcode-cn.com/articles/cat-and-mouse/)

[回到目录](../README.md)