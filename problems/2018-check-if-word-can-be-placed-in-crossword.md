# 2018. check-if-word-can-be-placed-in-crossword | 判断单词是否能放入填字游戏内

## Question description

<!--If you want to use the English description, use <p>You are given an <code>m x n</code> matrix <code>board</code>, representing the<strong> current </strong>state of a crossword puzzle. The crossword contains lowercase English letters (from solved words), <code>&#39; &#39;</code> to represent any <strong>empty </strong>cells, and <code>&#39;#&#39;</code> to represent any <strong>blocked</strong> cells.</p>

<p>A word can be placed<strong> horizontally</strong> (left to right <strong>or</strong> right to left) or <strong>vertically</strong> (top to bottom <strong>or</strong> bottom to top) in the board if:</p>

<ul>
	<li>It does not occupy a cell containing the character <code>&#39;#&#39;</code>.</li>
	<li>The cell each letter is placed in must either be <code>&#39; &#39;</code> (empty) or <strong>match</strong> the letter already on the <code>board</code>.</li>
	<li>There must not be any empty cells <code>&#39; &#39;</code> or other lowercase letters <strong>directly left or right</strong><strong> </strong>of the word if the word was placed <strong>horizontally</strong>.</li>
	<li>There must not be any empty cells <code>&#39; &#39;</code> or other lowercase letters <strong>directly above or below</strong> the word if the word was placed <strong>vertically</strong>.</li>
</ul>

<p>Given a string <code>word</code>, return <code>true</code><em> if </em><code>word</code><em> can be placed in </em><code>board</code><em>, or </em><code>false</code><em> <strong>otherwise</strong></em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/04/crossword-ex1-1.png" style="width: 478px; height: 180px;" />
<pre>
<strong>Input:</strong> board = [[&quot;#&quot;, &quot; &quot;, &quot;#&quot;], [&quot; &quot;, &quot; &quot;, &quot;#&quot;], [&quot;#&quot;, &quot;c&quot;, &quot; &quot;]], word = &quot;abc&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> The word &quot;abc&quot; can be placed as shown above (top to bottom).
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/04/crossword-ex2-1.png" style="width: 180px; height: 180px;" />
<pre>
<strong>Input:</strong> board = [[&quot; &quot;, &quot;#&quot;, &quot;a&quot;], [&quot; &quot;, &quot;#&quot;, &quot;c&quot;], [&quot; &quot;, &quot;#&quot;, &quot;a&quot;]], word = &quot;ac&quot;
<strong>Output:</strong> false
<strong>Explanation:</strong> It is impossible to place the word because there will always be a space/letter above or below it.</pre>

<p><strong>Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/10/04/crossword-ex3-1.png" style="width: 478px; height: 180px;" />
<pre>
<strong>Input:</strong> board = [[&quot;#&quot;, &quot; &quot;, &quot;#&quot;], [&quot; &quot;, &quot; &quot;, &quot;#&quot;], [&quot;#&quot;, &quot; &quot;, &quot;c&quot;]], word = &quot;ca&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> The word &quot;ca&quot; can be placed as shown above (right to left). 
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == board.length</code></li>
	<li><code>n == board[i].length</code></li>
	<li><code>1 &lt;= m * n &lt;= 2 * 10<sup>5</sup></code></li>
	<li><code>board[i][j]</code> will be <code>&#39; &#39;</code>, <code>&#39;#&#39;</code>, or a lowercase English letter.</li>
	<li><code>1 &lt;= word.length &lt;= max(m, n)</code></li>
	<li><code>word</code> will contain only lowercase English letters.</li>
</ul>
 instead-->
<p>给你一个&nbsp;<code>m x n</code>&nbsp;的矩阵&nbsp;<code>board</code>&nbsp;，它代表一个填字游戏&nbsp;<strong>当前</strong>&nbsp;的状态。填字游戏格子中包含小写英文字母（已填入的单词），表示&nbsp;<strong>空</strong>&nbsp;格的&nbsp;<code>' '</code>&nbsp;和表示&nbsp;<strong>障碍</strong>&nbsp;格子的&nbsp;<code>'#'</code>&nbsp;。</p>

<p>如果满足以下条件，那么我们可以 <strong>水平</strong>&nbsp;（从左到右 <strong>或者</strong>&nbsp;从右到左）或 <strong>竖直</strong>&nbsp;（从上到下 <strong>或者</strong>&nbsp;从下到上）填入一个单词：</p>

<ul>
	<li>该单词不占据任何&nbsp;<code>'#'</code>&nbsp;对应的格子。</li>
	<li>每个字母对应的格子要么是&nbsp;<code>' '</code>&nbsp;（空格）要么与 <code>board</code>&nbsp;中已有字母 <strong>匹配</strong>&nbsp;。</li>
	<li>如果单词是 <strong>水平</strong>&nbsp;放置的，那么该单词左边和右边 <strong>相邻</strong>&nbsp;格子不能为&nbsp;<code>' '</code>&nbsp;或小写英文字母。</li>
	<li>如果单词是&nbsp;<strong>竖直</strong>&nbsp;放置的，那么该单词上边和下边&nbsp;<strong>相邻</strong><strong>&nbsp;</strong>格子不能为&nbsp;<code>' '</code>&nbsp;或小写英文字母。</li>
</ul>

<p>给你一个字符串&nbsp;<code>word</code>&nbsp;，如果&nbsp;<code>word</code>&nbsp;可以被放入&nbsp;<code>board</code>&nbsp;中，请你返回&nbsp;<code>true</code>&nbsp;，否则请返回&nbsp;<code>false</code>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/09/18/crossword-1.png" style="width: 170px; height: 150px;" /></p>

<pre>
<b>输入：</b>board = [["#", " ", "#"], [" ", " ", "#"], ["#", "c", " "]], word = "abc"
<b>输出：</b>true
<b>解释：</b>单词 "abc" 可以如上图放置（从上往下）。
</pre>

<p><strong>示例 2：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/09/18/c2.png" style="width: 170px; height: 151px;" /></p>

<pre>
<b>输入：</b>board = [[" ", "#", "a"], [" ", "#", "c"], [" ", "#", "a"]], word = "ac"
<b>输出：</b>false
<b>解释：</b>无法放置单词，因为放置该单词后上方或者下方相邻格会有空格。</pre>

<p><strong>示例 3：</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/09/18/crossword-2.png" style="width: 171px; height: 146px;" /></p>

<pre>
<b>输入：</b>board = [["#", " ", "#"], [" ", " ", "#"], ["#", " ", "c"]], word = "ca"
<b>输出：</b>true
<b>解释：</b>单词 "ca" 可以如上图放置（从右到左）。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == board.length</code></li>
	<li><code>n == board[i].length</code></li>
	<li><code>1 &lt;= m * n &lt;= 2 * 10<sup>5</sup></code></li>
	<li><code>board[i][j]</code>&nbsp;可能为&nbsp;<code>' '</code>&nbsp;，<code>'#'</code>&nbsp;或者一个小写英文字母。</li>
	<li><code>1 &lt;= word.length &lt;= max(m, n)</code></li>
	<li><code>word</code>&nbsp;只包含小写英文字母。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 12 ms

```java
class Solution {

    boolean found = false;

    enum Direction{
        TOP, BOTTOM, LEFT, RIGHT
    }

    public boolean placeWordInCrossword(char[][] board, String word) {
        found = false;
        int m = board.length + 2, n = board[0].length + 2;

        // 添加外边界
        char[][] nBoard = new char[m][n];
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(i * j == 0 || i == m-1  || j == n-1){
                    nBoard[i][j] = '#';
                }else{
                    nBoard[i][j] = board[i-1][j-1];
                }
            }
        }
        board = nBoard;


        char[] chars = word.toCharArray();
        for(int row=1;row<m && !found;row++){
            for(int col=1;col<n && !found;col++){
                if(board[row][col] == ' ' || chars[0] == board[row][col] || chars[chars.length - 1] == board[row][col]){
                    // 单词正着方向探索放置
                    if(board[row][col] == ' ' || chars[0] == board[row][col]){
                        // 满足 相邻 格子不能为 ' ' 或小写英文字母时探索
                        if(bound(board[row-1][col])){
                            dfs(board, row, col, Direction.BOTTOM, chars, 1, true);
                        }
                        if(bound(board[row+1][col])){
                            dfs(board, row, col, Direction.TOP, chars, 1, true);
                        }
                        if(bound(board[row][col-1])){
                            dfs(board, row, col, Direction.RIGHT, chars, 1, true);
                        }
                        if(bound(board[row][col+1])){
                            dfs(board, row, col, Direction.LEFT, chars, 1, true);
                        }
                    }

                    // 单词反方向探索放置
                    if(board[row][col] == ' ' || chars[chars.length - 1] == board[row][col]){
                        if(bound(board[row-1][col])){
                            dfs(board, row, col, Direction.BOTTOM, chars, chars.length - 2, false);
                        }
                        if(bound(board[row+1][col])){
                            dfs(board, row, col, Direction.TOP, chars, chars.length - 2, false);
                        }
                        if(bound(board[row][col-1])){
                            dfs(board, row, col, Direction.RIGHT, chars, chars.length - 2, false);
                        }
                        if(bound(board[row][col+1])){
                            dfs(board, row, col, Direction.LEFT, chars, chars.length - 2, false);
                        }
                    }

                }
            }
        }

        return found;
    }


    /**
     *
     *
     * @param board
     * @param r 行索引
     * @param c 列索引
     * @param direction 放置方向
     * @param word  单词
     * @param point 当前放置到单词的索引位置
     * @param forword 单词放置方向
     */
    public void dfs(char[][] board, int r, int c, Direction direction, char[] word, int point, boolean forword){
        int m = board.length, n = board[0].length;

        // 下一个坐标的位置
        int row = r, col = c;
        switch (direction){
            case TOP: row--; break;
            case BOTTOM: row++; break;
            case LEFT: col--; break;
            case RIGHT: col++; break;
        }

        if(found){
            return ;
        }else if(bound(board[row][col])){   // 到达障碍物
            // 单词已经全部放完
            if((forword && point == word.length) || (!forword && point == -1)){
                found = true;
            }

            return ;
        }else{ // 未到到达障碍物
            // 单词已经全部放完
            if((forword && point == word.length) || (!forword && point == -1)){
                return ;
            }else if(board[row][col] == ' ' || board[row][col] == word[point]){ // 继续填单词
                dfs(board, row, col, direction, word, forword ? point + 1 : point - 1, forword);
            }
        }
    }

    /**
     * 是否为边界符号
     *
     * @param c
     * @return
     */
    public boolean bound(char c){
        if(c == ' ' || ('a' <= c && c <= 'z')){
            return false;
        }else{
            return true;
        }
    }

}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/check-if-word-can-be-placed-in-crossword/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/check-if-word-can-be-placed-in-crossword/description/)

Solution: [LeetCode](https://leetcode.com/articles/check-if-word-can-be-placed-in-crossword/)  /  [LeetCode中国](https://leetcode-cn.com/articles/check-if-word-can-be-placed-in-crossword/)

[回到目录](../README.md)