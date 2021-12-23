# 1449. form-largest-integer-with-digits-that-add-up-to-target | 数位成本和为目标值的最大数字

## Question description

<!--If you want to use the English description, use <p>Given an array of integers <code>cost</code> and an integer <code>target</code>. Return the <strong>maximum</strong> integer you can paint&nbsp;under the following rules:</p>

<ul>
	<li>The cost of painting a&nbsp;digit (i+1) is given by&nbsp;<code>cost[i]</code>&nbsp;(0 indexed).</li>
	<li>The total cost used must&nbsp;be equal to <code>target</code>.</li>
	<li>Integer does not have digits 0.</li>
</ul>

<p>Since the answer may be too large, return it as string.</p>

<p>If there is no way to paint any integer given the condition, return &quot;0&quot;.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> cost = [4,3,2,5,6,7,2,5,5], target = 9
<strong>Output:</strong> &quot;7772&quot;
<strong>Explanation: </strong> The cost to paint the digit &#39;7&#39; is 2, and the digit &#39;2&#39; is 3. Then cost(&quot;7772&quot;) = 2*3+ 3*1 = 9. You could also paint &quot;977&quot;, but &quot;7772&quot; is the largest number.
<strong>Digit    cost</strong>
  1  -&gt;   4
  2  -&gt;   3
  3  -&gt;   2
  4  -&gt;   5
  5  -&gt;   6
  6  -&gt;   7
  7  -&gt;   2
  8  -&gt;   5
  9  -&gt;   5
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> cost = [7,6,5,5,5,6,8,7,8], target = 12
<strong>Output:</strong> &quot;85&quot;
<strong>Explanation:</strong> The cost to paint the digit &#39;8&#39; is 7, and the digit &#39;5&#39; is 5. Then cost(&quot;85&quot;) = 7 + 5 = 12.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> cost = [2,4,6,2,4,6,4,4,4], target = 5
<strong>Output:</strong> &quot;0&quot;
<strong>Explanation:</strong> It&#39;s not possible to paint any integer with total cost equal to target.
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> cost = [6,10,15,40,40,40,40,40,40], target = 47
<strong>Output:</strong> &quot;32211&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>cost.length == 9</code></li>
	<li><code>1 &lt;= cost[i] &lt;= 5000</code></li>
	<li><code>1 &lt;= target &lt;= 5000</code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>cost</code> 和一个整数 <code>target</code> 。请你返回满足如下规则可以得到的 <strong>最大</strong> 整数：</p>

<ul>
	<li>给当前结果添加一个数位（<code>i + 1</code>）的成本为 <code>cost[i]</code> （<code>cost</code> 数组下标从 0 开始）。</li>
	<li>总成本必须恰好等于 <code>target</code> 。</li>
	<li>添加的数位中没有数字 0 。</li>
</ul>

<p>由于答案可能会很大，请你以字符串形式返回。</p>

<p>如果按照上述要求无法得到任何整数，请你返回 "0" 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>cost = [4,3,2,5,6,7,2,5,5], target = 9
<strong>输出：</strong>"7772"
<strong>解释：</strong>添加数位 '7' 的成本为 2 ，添加数位 '2' 的成本为 3 。所以 "7772" 的代价为 2*3+ 3*1 = 9 。 "977" 也是满足要求的数字，但 "7772" 是较大的数字。
<strong> 数字     成本</strong>
  1  ->   4
  2  ->   3
  3  ->   2
  4  ->   5
  5  ->   6
  6  ->   7
  7  ->   2
  8  ->   5
  9  ->   5
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>cost = [7,6,5,5,5,6,8,7,8], target = 12
<strong>输出：</strong>"85"
<strong>解释：</strong>添加数位 '8' 的成本是 7 ，添加数位 '5' 的成本是 5 。"85" 的成本为 7 + 5 = 12 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>cost = [2,4,6,2,4,6,4,4,4], target = 5
<strong>输出：</strong>"0"
<strong>解释：</strong>总成本是 target 的条件下，无法生成任何整数。
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>cost = [6,10,15,40,40,40,40,40,40], target = 47
<strong>输出：</strong>"32211"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>cost.length == 9</code></li>
	<li><code>1 <= cost[i] <= 5000</code></li>
	<li><code>1 <= target <= 5000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public String largestNumber(int[] cost, int target) {
        int[][] dp = new int[10][target + 1];
        for (int i = 0; i < 10; ++i) {
            Arrays.fill(dp[i], Integer.MIN_VALUE);
        }
        int[][] from = new int[10][target + 1];
        dp[0][0] = 0;
        for (int i = 0; i < 9; ++i) {
            int c = cost[i];
            for (int j = 0; j <= target; ++j) {
                if (j < c) {
                    dp[i + 1][j] = dp[i][j];
                    from[i + 1][j] = j;
                } else {
                    if (dp[i][j] > dp[i + 1][j - c] + 1) {
                        dp[i + 1][j] = dp[i][j];
                        from[i + 1][j] = j;
                    } else {
                        dp[i + 1][j] = dp[i + 1][j - c] + 1;
                        from[i + 1][j] = j - c;
                    }
                }
            }
        }
        if (dp[9][target] < 0) {
            return "0";
        }
        StringBuffer sb = new StringBuffer();
        int i = 9, j = target;
        while (i > 0) {
            if (j == from[i][j]) {
                --i;
            } else {
                sb.append(i);
                j = from[i][j];
            }
        }
        return sb.toString();
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/form-largest-integer-with-digits-that-add-up-to-target/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/form-largest-integer-with-digits-that-add-up-to-target/description/)

Solution: [LeetCode](https://leetcode.com/articles/form-largest-integer-with-digits-that-add-up-to-target/)  /  [LeetCode中国](https://leetcode-cn.com/articles/form-largest-integer-with-digits-that-add-up-to-target/)

[回到目录](../README.md)