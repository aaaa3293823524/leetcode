# 79. word-search | 单词搜索

## Question description

<!--If you want to use the English description, use <p>Given an&nbsp;<code>m x n</code> <code>board</code> and a <code>word</code>, find if the word exists in the grid.</p>

<p>The word can be constructed from letters of sequentially adjacent cells, where &quot;adjacent&quot; cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/word2.jpg" style="width: 322px; height: 242px;" />
<pre>
<strong>Input:</strong> board = [[&quot;A&quot;,&quot;B&quot;,&quot;C&quot;,&quot;E&quot;],[&quot;S&quot;,&quot;F&quot;,&quot;C&quot;,&quot;S&quot;],[&quot;A&quot;,&quot;D&quot;,&quot;E&quot;,&quot;E&quot;]], word = &quot;ABCCED&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg" style="width: 322px; height: 242px;" />
<pre>
<strong>Input:</strong> board = [[&quot;A&quot;,&quot;B&quot;,&quot;C&quot;,&quot;E&quot;],[&quot;S&quot;,&quot;F&quot;,&quot;C&quot;,&quot;S&quot;],[&quot;A&quot;,&quot;D&quot;,&quot;E&quot;,&quot;E&quot;]], word = &quot;SEE&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/15/word3.jpg" style="width: 322px; height: 242px;" />
<pre>
<strong>Input:</strong> board = [[&quot;A&quot;,&quot;B&quot;,&quot;C&quot;,&quot;E&quot;],[&quot;S&quot;,&quot;F&quot;,&quot;C&quot;,&quot;S&quot;],[&quot;A&quot;,&quot;D&quot;,&quot;E&quot;,&quot;E&quot;]], word = &quot;ABCB&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == board.length</code></li>
	<li><code>n = board[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 200</code></li>
	<li><code>1 &lt;= word.length &lt;= 10<sup>3</sup></code></li>
	<li><code>board</code>&nbsp;and <code>word</code> consists only of lowercase and uppercase English letters.</li>
</ul>
 instead-->
<p>给定一个二维网格和一个单词，找出该单词是否存在于网格中。</p>

<p>单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中&ldquo;相邻&rdquo;单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre>board =
[
  [&#39;A&#39;,&#39;B&#39;,&#39;C&#39;,&#39;E&#39;],
  [&#39;S&#39;,&#39;F&#39;,&#39;C&#39;,&#39;S&#39;],
  [&#39;A&#39;,&#39;D&#39;,&#39;E&#39;,&#39;E&#39;]
]

给定 word = &quot;<strong>ABCCED</strong>&quot;, 返回 <strong>true</strong>
给定 word = &quot;<strong>SEE</strong>&quot;, 返回 <strong>true</strong>
给定 word = &quot;<strong>ABCB</strong>&quot;, 返回 <strong>false</strong></pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>board</code> 和 <code>word</code> 中只包含大写和小写英文字母。</li>
	<li><code>1 &lt;= board.length &lt;= 200</code></li>
	<li><code>1 &lt;= board[i].length &lt;= 200</code></li>
	<li><code>1 &lt;= word.length &lt;= 10^3</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 19 ms

```java
class Solution {
int row;
    int col;
    char[][] board;
    String word;
    boolean[][] marked;

    public boolean exist(char[][] board, String word) {
        row = board.length;
        col = board[0].length;
        if (row == 0)
            return false;

        marked = new boolean[row][col];
        this.board = board;
        this.word = word;

        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                if (dfs(i, j, 0))
                    return true;
            }
        }
        return false;
    }

    public boolean dfs(int i, int j, int start) {
        if (start == word.length() - 1)
            return board[i][j] == word.charAt(start);

        if (board[i][j] == word.charAt(start)) {
            marked[i][j] = true;
            if (isVaild(i - 1, j) && !marked[i - 1][j] && dfs(i - 1, j, start + 1)) {
                return true;
            } else if (isVaild(i, j + 1) && !marked[i][j + 1] && dfs(i, j + 1, start + 1)) {
                return true;
            } else if (isVaild(i + 1, j) && !marked[i + 1][j] && dfs(i + 1, j, start + 1)) {
                return true;
            } else if (isVaild(i, j - 1) && !marked[i][j - 1] && dfs(i, j - 1, start + 1)) {
                return true;
            } else{
                marked[i][j] = false;
            }
        }
        return false;
    }

    public boolean isVaild(int i, int j) {
        return i >= 0 && i < row && j >= 0 && j < col;
    }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/word-search/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/word-search/description/)

Solution: [LeetCode](https://leetcode.com/articles/word-search/)  /  [LeetCode中国](https://leetcode-cn.com/articles/word-search/)

[回到目录](../README.md)