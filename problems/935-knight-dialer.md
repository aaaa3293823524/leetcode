# 935. knight-dialer | 骑士拨号器

## Question description

<!--If you want to use the English description, use <p>The chess knight has a <strong>unique movement</strong>,&nbsp;it may move two squares vertically and one square horizontally, or two squares horizontally and one square vertically (with both forming the shape of an <strong>L</strong>). The possible movements of chess knight are shown in this diagaram:</p>

<p>A chess knight can move as indicated in the chess diagram below:</p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/18/chess.jpg" style="width: 402px; height: 402px;" />
<p>We have a chess knight and a phone pad as shown below, the knight <strong>can only stand on a numeric cell</strong>&nbsp;(i.e. blue cell).</p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/18/phone.jpg" style="width: 242px; height: 322px;" />
<p>Given an integer <code>n</code>, return how many distinct phone numbers of length <code>n</code> we can dial.</p>

<p>You are allowed to place the knight <strong>on any numeric cell</strong> initially and then you should perform <code>n - 1</code> jumps to dial a number of length <code>n</code>. All jumps should be <strong>valid</strong> knight jumps.</p>

<p>As the answer may be very large, <strong>return the answer modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 1
<strong>Output:</strong> 10
<strong>Explanation:</strong> We need to dial a number of length 1, so placing the knight over any numeric cell of the 10 cells is sufficient.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 2
<strong>Output:</strong> 20
<strong>Explanation:</strong> All the valid number we can dial are [04, 06, 16, 18, 27, 29, 34, 38, 40, 43, 49, 60, 61, 67, 72, 76, 81, 83, 92, 94]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 3131
<strong>Output:</strong> 136006598
<strong>Explanation:</strong> Please take care of the mod.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 5000</code></li>
</ul>
 instead-->
<p>国际象棋中的骑士可以按下图所示进行移动：</p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/11/03/knight.png" style="height: 150px; width: 150px;">&nbsp;.&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/11/03/keypad.png" style="height: 150px; width: 134px;"></p>

<p><br>
这一次，我们将&nbsp;&ldquo;骑士&rdquo; 放在电话拨号盘的任意数字键（如上图所示）上，接下来，骑士将会跳&nbsp;N-1 步。每一步必须是从一个数字键跳到另一个数字键。</p>

<p>每当它落在一个键上（包括骑士的初始位置），都会拨出键所对应的数字，总共按下&nbsp;<code>N</code> 位数字。</p>

<p>你能用这种方式拨出多少个不同的号码？</p>

<p>因为答案可能很大，<strong>所以输出答案模&nbsp;<code>10^9 + 7</code></strong>。</p>

<p>&nbsp;</p>

<ul>
</ul>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>1
<strong>输出：</strong>10
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>2
<strong>输出：</strong>20
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>3
<strong>输出：</strong>46
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= N &lt;= 5000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 20 ms

```java
class Solution {
    public int knightDialer(int N) {
        int MOD = 1_000_000_007;
        int[][] moves = new int[][]{
            {4,6},{6,8},{7,9},{4,8},{3,9,0},
            {},{1,7,0},{2,6},{1,3},{2,4}};

        int[][] dp = new int[2][10];
        Arrays.fill(dp[0], 1);
        for (int hops = 0; hops < N-1; ++hops) {
            Arrays.fill(dp[~hops & 1], 0);
            for (int node = 0; node < 10; ++node)
                for (int nei: moves[node]) {
                    dp[~hops & 1][nei] += dp[hops & 1][node];
                    dp[~hops & 1][nei] %= MOD;
                }
        }

        long ans = 0;
        for (int x: dp[~N & 1])
            ans += x;
        return (int) (ans % MOD);
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/knight-dialer/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/knight-dialer/description/)

Solution: [LeetCode](https://leetcode.com/articles/knight-dialer/)  /  [LeetCode中国](https://leetcode-cn.com/articles/knight-dialer/)

[回到目录](../README.md)