# 1155. number-of-dice-rolls-with-target-sum | 掷骰子的N种方法

## Question description

<!--If you want to use the English description, use <p>You have <code>n</code> dice and each die has <code>k</code> faces numbered from <code>1</code> to <code>k</code>.</p>

<p>Given three integers <code>n</code>, <code>k</code>, and <code>target</code>, return <em>the number of possible ways (out of the </em><code>k<sup>n</sup></code><em> total ways) </em><em>to roll the dice so the sum of the face-up numbers equals </em><code>target</code>. Since the answer may be too large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 1, k = 6, target = 3
<strong>Output:</strong> 1
<strong>Explanation:</strong> You throw one die with 6 faces.
There is only one way to get a sum of 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 2, k = 6, target = 7
<strong>Output:</strong> 6
<strong>Explanation:</strong> You throw two dice, each with 6 faces.
There are 6 ways to get a sum of 7: 1+6, 2+5, 3+4, 4+3, 5+2, 6+1.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> n = 30, k = 30, target = 500
<strong>Output:</strong> 222616187
<strong>Explanation:</strong> The answer must be returned modulo 10<sup>9</sup> + 7.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n, k &lt;= 30</code></li>
	<li><code>1 &lt;= target &lt;= 1000</code></li>
</ul>
 instead-->
<p>这里有&nbsp;<code>d</code>&nbsp;个一样的骰子，每个骰子上都有&nbsp;<code>f</code>&nbsp;个面，分别标号为&nbsp;<code>1, 2, ..., f</code>。</p>

<p>我们约定：掷骰子的得到总点数为各骰子面朝上的数字的总和。</p>

<p>如果需要掷出的总点数为&nbsp;<code>target</code>，请你计算出有多少种不同的组合情况（所有的组合情况总共有 <code>f^d</code> 种），<strong>模&nbsp;<code>10^9 + 7</code></strong>&nbsp;后返回。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>d = 1, f = 6, target = 3
<strong>输出：</strong>1
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>d = 2, f = 6, target = 7
<strong>输出：</strong>6
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>d = 2, f = 5, target = 10
<strong>输出：</strong>1
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>d = 1, f = 2, target = 3
<strong>输出：</strong>0
</pre>

<p><strong>示例 5：</strong></p>

<pre><strong>输入：</strong>d = 30, f = 30, target = 500
<strong>输出：</strong>222616187</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= d, f &lt;= 30</code></li>
	<li><code>1 &lt;= target &lt;= 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 25 ms

```java
class Solution {
      private static final int MOD = 1000000007;
  public int numRollsToTarget(int d, int f, int target) {
    int[][] dp = new int[31][1001];
    int min = Math.min(f, target);
    for (int i = 1; i <= min; i++) {
      dp[1][i] = 1;
    }
    int targetMax = d * f;
    for (int i = 2; i <= d; i++) {
      for (int j = i; j <= targetMax; j++) {
        for (int k = 1; j - k >= 0 && k <= f; k++) {
          dp[i][j] = (dp[i][j] + dp[i - 1][j - k]) % MOD;
        }
      }
    }
    return dp[d][target];
  }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/number-of-dice-rolls-with-target-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/number-of-dice-rolls-with-target-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/number-of-dice-rolls-with-target-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/number-of-dice-rolls-with-target-sum/)

[回到目录](../README.md)