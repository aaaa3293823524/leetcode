# 剑指 Offer 13. ji-qi-ren-de-yun-dong-fan-wei-lcof | 机器人的运动范围

## Question description

<!--If you want to use the English description, use English description is not available for the problem. Please switch to Chinese. instead-->
<p>地上有一个m行n列的方格，从坐标 <code>[0,0]</code> 到坐标 <code>[m-1,n-1]</code> 。一个机器人从坐标 <code>[0, 0] </code>的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>m = 2, n = 3, k = 1
<strong>输出：</strong>3
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>m = 3, n = 1, k = 0
<strong>输出：</strong>1
</pre>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n,m &lt;= 100</code></li>
	<li><code>0 &lt;= k&nbsp;&lt;= 20</code></li>
</ul>


## Note

广度优先遍历


## Solution

Language: **java**  /  Runtime: 5 ms

```java
class Solution {
    public int movingCount(int m, int n, int k) {
        if (k == 0) {
            return 1;
        }
        Queue<int[]> queue = new LinkedList<int[]>();
        // 向右和向下的方向数组
        int[] dx = {0, 1};
        int[] dy = {1, 0};
        boolean[][] vis = new boolean[m][n];
        queue.offer(new int[]{0, 0});
        vis[0][0] = true;
        int ans = 1;
        while (!queue.isEmpty()) {
            int[] cell = queue.poll();
            int x = cell[0], y = cell[1];
            for (int i = 0; i < 2; ++i) {
                int tx = dx[i] + x;
                int ty = dy[i] + y;
                if (tx < 0 || tx >= m || ty < 0 || ty >= n || vis[tx][ty] || get(tx) + get(ty) > k) {
                    continue;
                }
                queue.offer(new int[]{tx, ty});
                vis[tx][ty] = true;
                ans++;
            }
        }
        return ans;
    }

    private int get(int x) {
        int res = 0;
        while (x != 0) {
            res += x % 10;
            x /= 10;
        }
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/description/)

Solution: [LeetCode](https://leetcode.com/articles/ji-qi-ren-de-yun-dong-fan-wei-lcof/)  /  [LeetCode中国](https://leetcode-cn.com/articles/ji-qi-ren-de-yun-dong-fan-wei-lcof/)

[回到目录](../README.md)