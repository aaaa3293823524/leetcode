# 813. largest-sum-of-averages | 最大平均值和的分组

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>nums</code> and an integer <code>k</code>. You can partition the array into <strong>at most</strong> <code>k</code> non-empty adjacent subarrays. The <strong>score</strong> of a partition is the sum of the averages of each subarray.</p>

<p>Note that the partition must use every integer in <code>nums</code>, and that the score is not necessarily an integer.</p>

<p>Return <em>the maximum <strong>score</strong> you can achieve of all the possible partitions</em>. Answers within <code>10<sup>-6</sup></code> of the actual answer will be accepted.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [9,1,2,3,9], k = 3
<strong>Output:</strong> 20.00000
<strong>Explanation:</strong> 
The best choice is to partition nums into [9], [1, 2, 3], [9]. The answer is 9 + (1 + 2 + 3) / 3 + 9 = 20.
We could have also partitioned nums into [9, 1], [2], [3, 9], for example.
That partition would lead to a score of 5 + 2 + 6 = 13, which is worse.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5,6,7], k = 4
<strong>Output:</strong> 20.50000
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 100</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= k &lt;= nums.length</code></li>
</ul>
 instead-->
<p>我们将给定的数组&nbsp;<code>A</code>&nbsp;分成&nbsp;<code>K</code>&nbsp;个相邻的非空子数组 ，我们的分数由每个子数组内的平均值的总和构成。计算我们所能得到的最大分数是多少。</p>

<p>注意我们必须使用 A 数组中的每一个数进行分组，并且分数不一定需要是整数。</p>

<pre>
<strong>示例:</strong>
<strong>输入:</strong> 
A = [9,1,2,3,9]
K = 3
<strong>输出:</strong> 20
<strong>解释:</strong> 
A 的最优分组是[9], [1, 2, 3], [9]. 得到的分数是 9 + (1 + 2 + 3) / 3 + 9 = 20.
我们也可以把 A 分成[9, 1], [2], [3, 9].
这样的分组得到的分数为 5 + 2 + 6 = 13, 但不是最大值.
</pre>

<p><strong>说明: </strong></p>

<ul>
	<li><code>1 &lt;= A.length &lt;= 100</code>.</li>
	<li><code>1 &lt;= A[i] &lt;= 10000</code>.</li>
	<li><code>1 &lt;= K &lt;= A.length</code>.</li>
	<li>答案误差在&nbsp;<code>10^-6</code>&nbsp;内被视为是正确的。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public double largestSumOfAverages(int[] A, int K) {
        int N = A.length;
        double[] P = new double[N+1];
        for (int i = 0; i < N; ++i)
            P[i+1] = P[i] + A[i];

        double[] dp = new double[N];
        for (int i = 0; i < N; ++i)
            dp[i] = (P[N] - P[i]) / (N - i);

        for (int k = 0; k < K-1; ++k)
            for (int i = 0; i < N; ++i)
                for (int j = i+1; j < N; ++j)
                    dp[i] = Math.max(dp[i], (P[j]-P[i]) / (j-i) + dp[j]);

        return dp[0];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/largest-sum-of-averages/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/largest-sum-of-averages/description/)

Solution: [LeetCode](https://leetcode.com/articles/largest-sum-of-averages/)  /  [LeetCode中国](https://leetcode-cn.com/articles/largest-sum-of-averages/)

[回到目录](../README.md)