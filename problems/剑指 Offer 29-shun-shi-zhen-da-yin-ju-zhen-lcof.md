# 剑指 Offer 29. shun-shi-zhen-da-yin-ju-zhen-lcof | 顺时针打印矩阵

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>matrix = [[1,2,3],[4,5,6],[7,8,9]]
<strong>输出：</strong>[1,2,3,6,9,8,7,4,5]
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>matrix =&nbsp;[[1,2,3,4],[5,6,7,8],[9,10,11,12]]
<strong>输出：</strong>[1,2,3,4,8,12,11,10,9,5,6,7]
</pre>

<p>&nbsp;</p>

<p><strong>限制：</strong></p>

<ul>
	<li><code>0 &lt;= matrix.length &lt;= 100</code></li>
	<li><code>0 &lt;= matrix[i].length&nbsp;&lt;= 100</code></li>
</ul>

<p>注意：本题与主站 54 题相同：<a href="https://leetcode-cn.com/problems/spiral-matrix/">https://leetcode-cn.com/problems/spiral-matrix/</a></p>




## Solution

Language: **java**  /  Runtime: 4 ms

```java
class Solution {
    public int[] spiralOrder(int[][] matrix) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return new int[0];
        }
        int rows = matrix.length, columns = matrix[0].length;
        boolean[][] visited = new boolean[rows][columns];
        int total = rows * columns;
        int[] order = new int[total];
        int row = 0, column = 0;
        int[][] directions = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
        int directionIndex = 0;
        for (int i = 0; i < total; i++) {
            order[i] = matrix[row][column];
            visited[row][column] = true;
            int nextRow = row + directions[directionIndex][0], nextColumn = column + directions[directionIndex][1];
            if (nextRow < 0 || nextRow >= rows || nextColumn < 0 || nextColumn >= columns || visited[nextRow][nextColumn]) {
                directionIndex = (directionIndex + 1) % 4;
            }
            row += directions[directionIndex][0];
            column += directions[directionIndex][1];
        }
        return order;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/shun-shi-zhen-da-yin-ju-zhen-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/shun-shi-zhen-da-yin-ju-zhen-lcof/)

[回到目录](../README.md)