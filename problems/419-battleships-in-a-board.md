# 419. battleships-in-a-board | 甲板上的战舰

## Question description

<!--If you want to use the English description, use <p>Given an <code>m x n</code> matrix <code>board</code> where each cell is a battleship <code>&#39;X&#39;</code> or empty <code>&#39;.&#39;</code>, return <em>the number of the <strong>battleships</strong> on</em> <code>board</code>.</p>

<p><strong>Battleships</strong> can only be placed horizontally or vertically on <code>board</code>. In other words, they can only be made of the shape <code>1 x k</code> (<code>1</code> row, <code>k</code> columns) or <code>k x 1</code> (<code>k</code> rows, <code>1</code> column), where <code>k</code> can be of any size. At least one horizontal or vertical cell separates between two battleships (i.e., there are no adjacent battleships).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/10/battelship-grid.jpg" style="width: 333px; height: 333px;" />
<pre>
<strong>Input:</strong> board = [[&quot;X&quot;,&quot;.&quot;,&quot;.&quot;,&quot;X&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;X&quot;],[&quot;.&quot;,&quot;.&quot;,&quot;.&quot;,&quot;X&quot;]]
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> board = [[&quot;.&quot;]]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == board.length</code></li>
	<li><code>n == board[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 200</code></li>
	<li><code>board[i][j]</code> is either <code>&#39;.&#39;</code> or <code>&#39;X&#39;</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you do it in one-pass, using only <code>O(1)</code> extra memory and without modifying the values <code>board</code>?</p>
 instead-->
<p>给你一个大小为 <code>m x n</code> 的矩阵 <code>board</code> 表示甲板，其中，每个单元格可以是一艘战舰 <code>'X'</code> 或者是一个空位 <code>'.'</code> ，返回在甲板 <code>board</code> 上放置的 <strong>战舰</strong> 的数量。</p>

<p><strong>战舰</strong> 只能水平或者垂直放置在 <code>board</code> 上。换句话说，战舰只能按 <code>1 x k</code>（<code>1</code> 行，<code>k</code> 列）或 <code>k x 1</code>（<code>k</code> 行，<code>1</code> 列）的形状建造，其中 <code>k</code> 可以是任意大小。两艘战舰之间至少有一个水平或垂直的空位分隔 （即没有相邻的战舰）。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/10/battelship-grid.jpg" style="width: 333px; height: 333px;" />
<pre>
<strong>输入：</strong>board = [["X",".",".","X"],[".",".",".","X"],[".",".",".","X"]]
<strong>输出：</strong>2
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>board = [["."]]
<strong>输出：</strong>0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == board.length</code></li>
	<li><code>n == board[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 200</code></li>
	<li><code>board[i][j]</code> 是 <code>'.'</code> 或 <code>'X'</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>进阶：</strong>你可以实现一次扫描算法，并只使用<strong> </strong><code>O(1)</code><strong> </strong>额外空间，并且不修改 <code>board</code> 的值来解决这个问题吗？</p>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int countBattleships(char[][] board) {
        int m = board.length;
        int n = board[0].length;
        int res  = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (board[i][j] == 'X') {
                    if ((i <= 0 || board[i - 1][j] != 'X') && (j <= 0 || board[i][j - 1] != 'X')) res++;
                }
            }
        }
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/battleships-in-a-board/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/battleships-in-a-board/description/)

Solution: [LeetCode](https://leetcode.com/articles/battleships-in-a-board/)  /  [LeetCode中国](https://leetcode-cn.com/articles/battleships-in-a-board/)

[回到目录](../README.md)