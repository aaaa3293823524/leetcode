# 1301. number-of-paths-with-max-score | 最大得分的路径数目

## Question description

<!--If you want to use the English description, use <p>You are given a square <code>board</code>&nbsp;of characters. You can move on the board starting at the bottom right square marked with the character&nbsp;<code>&#39;S&#39;</code>.</p>

<p>You need&nbsp;to reach the top left square marked with the character <code>&#39;E&#39;</code>. The rest of the squares are labeled either with a numeric character&nbsp;<code>1, 2, ..., 9</code> or with an obstacle <code>&#39;X&#39;</code>. In one move you can go up, left or up-left (diagonally) only if there is no obstacle there.</p>

<p>Return a list of two integers: the first integer is the maximum sum of numeric characters you can collect, and the second is the number of such paths that you can take to get that maximum sum, <strong>taken modulo <code>10^9 + 7</code></strong>.</p>

<p>In case there is no path, return&nbsp;<code>[0, 0]</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> board = ["E23","2X2","12S"]
<strong>Output:</strong> [7,1]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> board = ["E12","1X1","21S"]
<strong>Output:</strong> [4,2]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> board = ["E11","XXX","11S"]
<strong>Output:</strong> [0,0]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= board.length == board[i].length &lt;= 100</code></li>
</ul> instead-->
<p>给你一个正方形字符数组&nbsp;<code>board</code>&nbsp;，你从数组最右下方的字符&nbsp;<code>&#39;S&#39;</code>&nbsp;出发。</p>

<p>你的目标是到达数组最左上角的字符&nbsp;<code>&#39;E&#39;</code> ，数组剩余的部分为数字字符&nbsp;<code>1, 2, ..., 9</code>&nbsp;或者障碍 <code>&#39;X&#39;</code>。在每一步移动中，你可以向上、向左或者左上方移动，可以移动的前提是到达的格子没有障碍。</p>

<p>一条路径的 「得分」 定义为：路径上所有数字的和。</p>

<p>请你返回一个列表，包含两个整数：第一个整数是 「得分」 的最大值，第二个整数是得到最大得分的方案数，请把结果对&nbsp;<strong><code>10^9 + 7</code></strong> <strong>取余</strong>。</p>

<p>如果没有任何路径可以到达终点，请返回&nbsp;<code>[0, 0]</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>board = [&quot;E23&quot;,&quot;2X2&quot;,&quot;12S&quot;]
<strong>输出：</strong>[7,1]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>board = [&quot;E12&quot;,&quot;1X1&quot;,&quot;21S&quot;]
<strong>输出：</strong>[4,2]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>board = [&quot;E11&quot;,&quot;XXX&quot;,&quot;11S&quot;]
<strong>输出：</strong>[0,0]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= board.length == board[i].length &lt;= 100</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 23 ms

```java
class Solution {
    public int[] pathsWithMaxScore(List<String> board) {
        int mod = (int)1e9 + 7, len = board.size();
        int[][] f = new int[len][len];
        int[][] g = new int[len][len];
        for(int i = 0;i < len;i++)
            Arrays.fill(g[i], 1);
        for(int i = len - 1;i >= 0;i--) {
            for(int j = len - 1;j >= 0;j--) {
                char c = board.get(i).charAt(j);
                if(c != 'X') {
                    if(i + 1 < len && board.get(i + 1).charAt(j) != 'X') {
                        if((f[i + 1][j] > 0 || board.get(i + 1).charAt(j) == 'S') && f[i][j] < f[i + 1][j] + c - '0') {
                            f[i][j] = f[i + 1][j] + c - '0';
                            f[i][j] %= mod;
                            g[i][j] = g[i + 1][j];
                        }
                        else if(f[i][j] == f[i + 1][j] + c - '0') {
                            g[i][j] += g[i + 1][j];
                            g[i][j] %= mod;
                        }
                    }
                    if(j + 1 < len && board.get(i).charAt(j + 1) != 'X') {
                        if((f[i][j + 1] > 0 || board.get(i).charAt(j + 1) == 'S') && f[i][j] < f[i][j + 1] + c - '0') {
                            f[i][j] = f[i][j + 1] + c - '0';
                            f[i][j] %= mod;
                            g[i][j] = g[i][j + 1];
                        }
                        else if(f[i][j] == f[i][j + 1] + c - '0') {
                            g[i][j] += g[i][j + 1];
                            g[i][j] %= mod;
                        }
                    }
                    if(i + 1 < len && j + 1 < len && board.get(i + 1).charAt(j + 1) != 'X') {
                        if((f[i + 1][j + 1] > 0 || board.get(i + 1).charAt(j + 1) == 'S') && f[i][j] < f[i + 1][j + 1] + c - '0') {
                            f[i][j] = f[i + 1][j + 1] + c - '0';
                            f[i][j] %= mod;
                            g[i][j] = g[i + 1][j + 1];
                        }
                        else if(f[i][j] == f[i + 1][j + 1] + c - '0') {
                            g[i][j] += g[i + 1][j + 1];
                            g[i][j] %= mod;
                        }
                    }
                }
            }
        }
        return f[0][0] == 0 ? new int[]{0, 0} : new int[]{f[0][0] - 'E' + '0', g[0][0]};
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-paths-with-max-score/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-paths-with-max-score/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-paths-with-max-score/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-paths-with-max-score/)

[回到目录](../README.md)