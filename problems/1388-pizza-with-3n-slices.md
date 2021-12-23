# 1388. pizza-with-3n-slices | 3n 块披萨

## Question description

<!--If you want to use the English description, use <p>There is a pizza with 3n slices of varying size, you and your friends will take slices of pizza as follows:</p>

<ul>
	<li>You will pick <strong>any</strong> pizza slice.</li>
	<li>Your friend Alice&nbsp;will pick&nbsp;next slice in anti clockwise direction of your pick.&nbsp;</li>
	<li>Your friend Bob&nbsp;will&nbsp;pick&nbsp;next slice in clockwise direction of your pick.</li>
	<li>Repeat&nbsp;until&nbsp;there are no more slices of pizzas.</li>
</ul>

<p>Sizes of Pizza slices is represented by circular array <code>slices</code> in clockwise direction.</p>

<p>Return the maximum possible sum of slice sizes which you can have.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2020/02/18/sample_3_1723.png" style="width: 475px; height: 240px;" /></p>

<pre>
<strong>Input:</strong> slices = [1,2,3,4,5,6]
<strong>Output:</strong> 10
<strong>Explanation:</strong> Pick pizza slice of size 4, Alice and Bob will pick slices with size 3 and 5 respectively. Then Pick slices with size 6, finally Alice and Bob will pick slice of size 2 and 1 respectively. Total = 4 + 6.
</pre>

<p><strong>Example 2:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2020/02/18/sample_4_1723.png" style="width: 475px; height: 250px;" /></strong></p>

<pre>
<strong>Input:</strong> slices = [8,9,8,6,1,1]
<strong>Output:</strong> 16
<strong>Output:</strong> Pick pizza slice of size 8 in each turn. If you pick slice with size 9 your partners will pick slices of size 8.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> slices = [4,1,2,5,8,3,1,9,7]
<strong>Output:</strong> 21
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> slices = [3,1,2]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= slices.length &lt;= 500</code></li>
	<li><code>slices.length % 3 == 0</code></li>
	<li><code>1 &lt;= slices[i] &lt;= 1000</code></li>
</ul>
 instead-->
<p>给你一个披萨，它由 3n 块不同大小的部分组成，现在你和你的朋友们需要按照如下规则来分披萨：</p>

<ul>
	<li>你挑选 <strong>任意</strong>&nbsp;一块披萨。</li>
	<li>Alice 将会挑选你所选择的披萨逆时针方向的下一块披萨。</li>
	<li>Bob 将会挑选你所选择的披萨顺时针方向的下一块披萨。</li>
	<li>重复上述过程直到没有披萨剩下。</li>
</ul>

<p>每一块披萨的大小按顺时针方向由循环数组 <code>slices</code>&nbsp;表示。</p>

<p>请你返回你可以获得的披萨大小总和的最大值。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/03/21/sample_3_1723.png" style="height: 240px; width: 475px;"></p>

<pre><strong>输入：</strong>slices = [1,2,3,4,5,6]
<strong>输出：</strong>10
<strong>解释：</strong>选择大小为 4 的披萨，Alice 和 Bob 分别挑选大小为 3 和 5 的披萨。然后你选择大小为 6 的披萨，Alice 和 Bob 分别挑选大小为 2 和 1 的披萨。你获得的披萨总大小为 4 + 6 = 10 。
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/03/21/sample_4_1723.png" style="height: 250px; width: 475px;"></strong></p>

<pre><strong>输入：</strong>slices = [8,9,8,6,1,1]
<strong>输出：</strong>16
<strong>解释：</strong>两轮都选大小为 8 的披萨。如果你选择大小为 9 的披萨，你的朋友们就会选择大小为 8 的披萨，这种情况下你的总和不是最大的。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>slices = [4,1,2,5,8,3,1,9,7]
<strong>输出：</strong>21
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>slices = [3,1,2]
<strong>输出：</strong>3
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= slices.length &lt;= 500</code></li>
	<li><code>slices.length % 3 == 0</code></li>
	<li><code>1 &lt;= slices[i] &lt;= 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int maxSizeSlices(int[] slices) {
        int[] slices1 = new int[slices.length - 1];
        System.arraycopy(slices, 1, slices1, 0, slices.length - 1);
        int[] slices2 = new int[slices.length - 1];
        System.arraycopy(slices, 0, slices2, 0, slices.length - 1);
        int ans1 = calculate(slices1);
        int ans2 = calculate(slices2);
        return Math.max(ans1, ans2);
    }

    public int calculate(int[] slices) {
        int n = slices.length;
        int choose = (n + 1) / 3;
        int[][] dp = new int[n + 1][choose + 1];
        for (int i = 1; i <= n; ++i) {
            for (int j = 1; j <= choose; ++j) {
                dp[i][j] = Math.max(dp[i - 1][j], (i - 2 >= 0 ? dp[i - 2][j - 1] : 0) + slices[i - 1]);
            }
        }
        return dp[n][choose];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/pizza-with-3n-slices/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/pizza-with-3n-slices/description/)

Solution: [LeetCode](https://leetcode.com/articles/pizza-with-3n-slices/)  /  [LeetCode中国](https://leetcode-cn.com/articles/pizza-with-3n-slices/)

[回到目录](../README.md)