# 1659. maximize-grid-happiness | 最大化网格幸福感

## Question description

<!--If you want to use the English description, use <p>You are given four integers, <code>m</code>, <code>n</code>, <code>introvertsCount</code>, and <code>extrovertsCount</code>. You have an <code>m x n</code> grid, and there are two types of people: introverts and extroverts. There are <code>introvertsCount</code> introverts and <code>extrovertsCount</code> extroverts.</p>

<p>You should decide how many people you want to live in the grid and assign each of them one grid cell. Note that you <strong>do not</strong> have to have all the people living in the grid.</p>

<p>The <strong>happiness</strong> of each person is calculated as follows:</p>

<ul>
	<li>Introverts <strong>start</strong> with <code>120</code> happiness and <strong>lose</strong> <code>30</code> happiness for each neighbor (introvert or extrovert).</li>
	<li>Extroverts <strong>start</strong> with <code>40</code> happiness and <strong>gain</strong> <code>20</code> happiness for each neighbor (introvert or extrovert).</li>
</ul>

<p>Neighbors live in the directly adjacent cells north, east, south, and west of a person&#39;s cell.</p>

<p>The <strong>grid happiness</strong> is the <strong>sum</strong> of each person&#39;s happiness. Return<em> the <strong>maximum possible grid happiness</strong>.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/05/grid_happiness.png" style="width: 261px; height: 121px;" />
<pre>
<strong>Input:</strong> m = 2, n = 3, introvertsCount = 1, extrovertsCount = 2
<strong>Output:</strong> 240
<strong>Explanation:</strong> Assume the grid is 1-indexed with coordinates (row, column).
We can put the introvert in cell (1,1) and put the extroverts in cells (1,3) and (2,3).
- Introvert at (1,1) happiness: 120 (starting happiness) - (0 * 30) (0 neighbors) = 120
- Extrovert at (1,3) happiness: 40 (starting happiness) + (1 * 20) (1 neighbor) = 60
- Extrovert at (2,3) happiness: 40 (starting happiness) + (1 * 20) (1 neighbor) = 60
The grid happiness is 120 + 60 + 60 = 240.
The above figure shows the grid in this example with each person&#39;s happiness. The introvert stays in the light green cell while the extroverts live on the light purple cells.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> m = 3, n = 1, introvertsCount = 2, extrovertsCount = 1
<strong>Output:</strong> 260
<strong>Explanation:</strong> Place the two introverts in (1,1) and (3,1) and the extrovert at (2,1).
- Introvert at (1,1) happiness: 120 (starting happiness) - (1 * 30) (1 neighbor) = 90
- Extrovert at (2,1) happiness: 40 (starting happiness) + (2 * 20) (2 neighbors) = 80
- Introvert at (3,1) happiness: 120 (starting happiness) - (1 * 30) (1 neighbor) = 90
The grid happiness is 90 + 80 + 90 = 260.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> m = 2, n = 2, introvertsCount = 4, extrovertsCount = 0
<strong>Output:</strong> 240
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= m, n &lt;= 5</code></li>
	<li><code>0 &lt;= introvertsCount, extrovertsCount &lt;= min(m * n, 6)</code></li>
</ul>
 instead-->
<p>给你四个整数 <code>m</code>、<code>n</code>、<code>introvertsCount</code> 和 <code>extrovertsCount</code> 。有一个 <code>m x n</code> 网格，和两种类型的人：内向的人和外向的人。总共有 <code>introvertsCount</code> 个内向的人和 <code>extrovertsCount</code> 个外向的人。</p>

<p>请你决定网格中应当居住多少人，并为每个人分配一个网格单元。 注意，<strong>不必</strong> 让所有人都生活在网格中。</p>

<p>每个人的 <strong>幸福感</strong> 计算如下：</p>

<ul>
	<li>内向的人 <strong>开始</strong> 时有 <code>120</code> 个幸福感，但每存在一个邻居（内向的或外向的）他都会 <strong>失去</strong>  <code>30</code> 个幸福感。</li>
	<li>外向的人 <strong>开始</strong> 时有 <code>40</code> 个幸福感，每存在一个邻居（内向的或外向的）他都会 <strong>得到</strong>  <code>20</code> 个幸福感。</li>
</ul>

<p>邻居是指居住在一个人所在单元的上、下、左、右四个直接相邻的单元中的其他人。</p>

<p><strong>网格幸福感</strong> 是每个人幸福感的 <strong>总和</strong> 。 返回 <strong>最大可能的网格幸福感</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/11/15/grid_happiness.png" style="width: 261px; height: 121px;" />
<pre>
<strong>输入：</strong>m = 2, n = 3, introvertsCount = 1, extrovertsCount = 2
<strong>输出：</strong>240
<strong>解释：</strong>假设网格坐标 (row, column) 从 1 开始编号。
将内向的人放置在单元 (1,1) ，将外向的人放置在单元 (1,3) 和 (2,3) 。
- 位于 (1,1) 的内向的人的幸福感：120（初始幸福感）- (0 * 30)（0 位邻居）= 120
- 位于 (1,3) 的外向的人的幸福感：40（初始幸福感）+ (1 * 20)（1 位邻居）= 60
- 位于 (2,3) 的外向的人的幸福感：40（初始幸福感）+ (1 * 20)（1 位邻居）= 60
网格幸福感为：120 + 60 + 60 = 240
上图展示该示例对应网格中每个人的幸福感。内向的人在浅绿色单元中，而外向的人在浅紫色单元中。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>m = 3, n = 1, introvertsCount = 2, extrovertsCount = 1
<strong>输出：</strong>260
<strong>解释：</strong>将内向的人放置在单元 (1,1) 和 (3,1) ，将外向的人放置在单元 (2,1) 。
- 位于 (1,1) 的内向的人的幸福感：120（初始幸福感）- (1 * 30)（1 位邻居）= 90
- 位于 (2,1) 的外向的人的幸福感：40（初始幸福感）+ (2 * 20)（2 位邻居）= 80
- 位于 (3,1) 的内向的人的幸福感：120（初始幸福感）- (1 * 30)（1 位邻居）= 90
网格幸福感为 90 + 80 + 90 = 260
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>m = 2, n = 2, introvertsCount = 4, extrovertsCount = 0
<strong>输出：</strong>240
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= m, n <= 5</code></li>
	<li><code>0 <= introvertsCount, extrovertsCount <= min(m * n, 6)</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 231 ms

```java
class Solution {

    private int statemax = 1;
    private int[][][][] dp;
    private int[][] score, fix;
    private int[] inCnt, exCnt;

    public int getMaxGridHappiness(int m, int n, int introvertsCount, int extrovertsCount) {

        for(int i = 0; i < n; i ++)
            statemax *= 3;

        // 预处理 score 和 fix
        score = new int[statemax][statemax];
        fix = new int[statemax][statemax];
        for(int state1 = 0; state1 < statemax; state1 ++){

            int[] v1 = getStateArray(state1, n);
            for(int state2 = 0; state2 < statemax; state2 ++){

                int[] v2 = getStateArray(state2, n);
                score[state1][state2] = getScore(v1, v2, n);
                fix[state1][state2] = getFix(v1, v2, n);
            }
        }

        // 预处理每个状态的内向人数和外向人数
        inCnt = new int[statemax];
        exCnt = new int[statemax];
        for(int state = 0; state < statemax; state ++)
            getInAndEx(state);

        dp = new int[m + 1][introvertsCount + 1][extrovertsCount + 1][statemax];
        return dfs(m, introvertsCount, extrovertsCount, 0);
    }

    // 记忆化搜索
    private int dfs(int leftrow, int in, int ex, int last){

        if(leftrow == 0) return 0;
        if(in == 0 && ex == 0) return 0;

        if(dp[leftrow][in][ex][last] != 0)
            return dp[leftrow][in][ex][last];

        int res = 0;
        for(int state = 0; state < statemax; state ++){
            // in 和 ex 人数够用，可以安排，则进行状态转移
            if(in >= inCnt[state] && ex >= exCnt[state])
                res = Math.max(res, score[state][last] + fix[last][state] + dfs(leftrow - 1, in - inCnt[state], ex - exCnt[state], state));
        }
        return dp[leftrow][in][ex][last] = res;
    }

    // 下面都是各种预处理需要的辅助函数
    private int[] getStateArray(int state, int col){

        int[] res = new int[col];
        for(int i = 0; i < col; i ++){
            res[i] = state % 3;
            state /= 3;
        }
        return res;
    }

    private int getScore(int[] curv, int[] lastv, int col){

        int res = 0, t = 0;
        for(int i = 0; i < col; i ++){
            t = 0;
            if(curv[i] == 1){
                t = 120;
                if(i > 0 && curv[i - 1] != 0) t -= 30;
                if(lastv[i] != 0) t -= 30;
                if(i + 1 < col && curv[i + 1] != 0) t -= 30;
            }
            else if(curv[i] == 2){
                t = 40;
                if(i > 0 && curv[i - 1] != 0) t += 20;
                if(lastv[i] != 0) t += 20;
                if(i + 1 < col && curv[i + 1] != 0) t += 20;
            }
            res += t;
        }
        return res;
    }

    private int getFix(int[] curv, int[] lastv, int col){

        int res = 0;
        for(int i = 0; i < col; i ++)
            if(curv[i] == 1 && lastv[i] != 0) res -= 30;
            else if(curv[i] == 2 && lastv[i] != 0) res += 20;
        return res;
    }

    private void getInAndEx(int state){

        int in = 0, ex = 0, x = state;
        while(x != 0){
            if(x % 3 == 1) inCnt[state] ++;
            else if(x % 3 == 2) exCnt[state] ++;
            x /= 3;
        }
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximize-grid-happiness/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximize-grid-happiness/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximize-grid-happiness/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximize-grid-happiness/)

[回到目录](../README.md)