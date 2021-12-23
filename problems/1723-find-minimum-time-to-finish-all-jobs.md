# 1723. find-minimum-time-to-finish-all-jobs | 完成所有工作的最短时间

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>jobs</code>, where <code>jobs[i]</code> is the amount of time it takes to complete the <code>i<sup>th</sup></code> job.</p>

<p>There are <code>k</code> workers that you can assign jobs to. Each job should be assigned to <strong>exactly</strong> one worker. The <strong>working time</strong> of a worker is the sum of the time it takes to complete all jobs assigned to them. Your goal is to devise an optimal assignment such that the <strong>maximum working time</strong> of any worker is <strong>minimized</strong>.</p>

<p><em>Return the <strong>minimum</strong> possible <strong>maximum working time</strong> of any assignment. </em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> jobs = [3,2,3], k = 3
<strong>Output:</strong> 3
<strong>Explanation:</strong> By assigning each person one job, the maximum time is 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> jobs = [1,2,4,7,8], k = 2
<strong>Output:</strong> 11
<strong>Explanation:</strong> Assign the jobs the following way:
Worker 1: 1, 2, 8 (working time = 1 + 2 + 8 = 11)
Worker 2: 4, 7 (working time = 4 + 7 = 11)
The maximum working time is 11.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= jobs.length &lt;= 12</code></li>
	<li><code>1 &lt;= jobs[i] &lt;= 10<sup>7</sup></code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>jobs</code> ，其中 <code>jobs[i]</code> 是完成第 <code>i</code> 项工作要花费的时间。</p>

<p>请你将这些工作分配给 <code>k</code> 位工人。所有工作都应该分配给工人，且每项工作只能分配给一位工人。工人的 <strong>工作时间</strong> 是完成分配给他们的所有工作花费时间的总和。请你设计一套最佳的工作分配方案，使工人的 <strong>最大工作时间</strong> 得以 <strong>最小化</strong> 。</p>

<p>返回分配方案中尽可能 <strong>最小</strong> 的 <strong>最大工作时间</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>jobs = [3,2,3], k = 3
<strong>输出：</strong>3
<strong>解释：</strong>给每位工人分配一项工作，最大工作时间是 3 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>jobs = [1,2,4,7,8], k = 2
<strong>输出：</strong>11
<strong>解释：</strong>按下述方式分配工作：
1 号工人：1、2、8（工作时间 = 1 + 2 + 8 = 11）
2 号工人：4、7（工作时间 = 4 + 7 = 11）
最大工作时间是 11 。</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= k <= jobs.length <= 12</code></li>
	<li><code>1 <= jobs[i] <= 10<sup>7</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 104 ms

```java
class Solution {
    public int minimumTimeRequired(int[] jobs, int k) {
        int n = jobs.length;
        int[] sum = new int[1 << n];
        for (int i = 1; i < (1 << n); i++) {
            int x = Integer.numberOfTrailingZeros(i), y = i - (1 << x);
            sum[i] = sum[y] + jobs[x];
        }

        int[][] dp = new int[k][1 << n];
        for (int i = 0; i < (1 << n); i++) {
            dp[0][i] = sum[i];
        }

        for (int i = 1; i < k; i++) {
            for (int j = 0; j < (1 << n); j++) {
                int minn = Integer.MAX_VALUE;
                for (int x = j; x != 0; x = (x - 1) & j) {
                    minn = Math.min(minn, Math.max(dp[i - 1][j - x], sum[x]));
                }
                dp[i][j] = minn;
            }
        }
        return dp[k - 1][(1 << n) - 1];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-minimum-time-to-finish-all-jobs/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-minimum-time-to-finish-all-jobs/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-minimum-time-to-finish-all-jobs/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-minimum-time-to-finish-all-jobs/)

[回到目录](../README.md)