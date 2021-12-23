# 1911. maximum-alternating-subsequence-sum | 最大子序列交替和

## Question description

<!--If you want to use the English description, use <p>The <strong>alternating sum</strong> of a <strong>0-indexed</strong> array is defined as the <strong>sum</strong> of the elements at <strong>even</strong> indices <strong>minus</strong> the <strong>sum</strong> of the elements at <strong>odd</strong> indices.</p>

<ul>
	<li>For example, the alternating sum of <code>[4,2,5,3]</code> is <code>(4 + 5) - (2 + 3) = 4</code>.</li>
</ul>

<p>Given an array <code>nums</code>, return <em>the <strong>maximum alternating sum</strong> of any subsequence of </em><code>nums</code><em> (after <strong>reindexing</strong> the elements of the subsequence)</em>.</p>

<ul>
</ul>

<p>A <strong>subsequence</strong> of an array is a new array generated from the original array by deleting some elements (possibly none) without changing the remaining elements&#39; relative order. For example, <code>[2,7,4]</code> is a subsequence of <code>[4,<u>2</u>,3,<u>7</u>,2,1,<u>4</u>]</code> (the underlined elements), while <code>[2,4,2]</code> is not.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [<u>4</u>,<u>2</u>,<u>5</u>,3]
<strong>Output:</strong> 7
<strong>Explanation:</strong> It is optimal to choose the subsequence [4,2,5] with alternating sum (4 + 5) - 2 = 7.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,6,7,<u>8</u>]
<strong>Output:</strong> 8
<strong>Explanation:</strong> It is optimal to choose the subsequence [8] with alternating sum 8.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [<u>6</u>,2,<u>1</u>,2,4,<u>5</u>]
<strong>Output:</strong> 10
<strong>Explanation:</strong> It is optimal to choose the subsequence [6,1,5] with alternating sum (6 + 5) - 1 = 10.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul> instead-->
<p>一个下标从 <strong>0</strong> 开始的数组的 <strong>交替和</strong> 定义为 <strong>偶数</strong> 下标处元素之 <strong>和</strong> 减去 <strong>奇数</strong> 下标处元素之 <strong>和</strong> 。</p>

<ul>
	<li>比方说，数组 <code>[4,2,5,3]</code> 的交替和为 <code>(4 + 5) - (2 + 3) = 4</code> 。</li>
</ul>

<p>给你一个数组 <code>nums</code> ，请你返回 <code>nums</code> 中任意子序列的 <strong>最大交替和</strong> （子序列的下标 <strong>重新</strong> 从 0 开始编号）。</p>

<ul>
</ul>

<p>一个数组的 <strong>子序列</strong> 是从原数组中删除一些元素后（也可能一个也不删除）剩余元素不改变顺序组成的数组。比方说，<code>[2,7,4]</code> 是 <code>[4,<strong>2</strong>,3,<strong>7</strong>,2,1,<strong>4</strong>]</code> 的一个子序列（加粗元素），但是 <code>[2,4,2]</code> 不是。</p>

<p> </p>

<p><b>示例 1：</b></p>

<pre><b>输入：</b>nums = [<strong>4</strong>,<strong>2</strong>,<strong>5</strong>,3]
<b>输出：</b>7
<b>解释：</b>最优子序列为 [4,2,5] ，交替和为 (4 + 5) - 2 = 7 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>nums = [5,6,7,<strong>8</strong>]
<b>输出：</b>8
<b>解释：</b>最优子序列为 [8] ，交替和为 8 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>nums = [<strong>6</strong>,2,<strong>1</strong>,2,4,<strong>5</strong>]
<b>输出：</b>10
<b>解释：</b>最优子序列为 [6,1,5] ，交替和为 (6 + 5) - 1 = 10 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 32 ms

```java
class Solution {
    public long maxAlternatingSum(int[] nums) {
        int n = nums.length;
        //dp[i][j]代表区间[0, i]中任意子序列的最大交替和，j为0/1表示该子序列的最后一个元素下标为奇/偶
        long[][] dp = new long[n][2]; 
        dp[0][0] = 0; dp[0][1] = nums[0];
        for (int i = 1; i < n; i++) {
            //不使用当前元素：dp[i - 1][0]  使用当前元素作奇下标：dp[i - 1][1] - nums[i]
            dp[i][0] = Math.max(dp[i - 1][0], dp[i - 1][1] - nums[i]);
            //不使用当前元素：dp[i - 1][1]  使用当前元素作偶下标：dp[i - 1][0] + nums[i]
            dp[i][1] = Math.max(dp[i - 1][1], dp[i - 1][0] + nums[i]);
        }
        return Math.max(dp[n - 1][0], dp[n - 1][1]);
    }
}



```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-alternating-subsequence-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-alternating-subsequence-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-alternating-subsequence-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-alternating-subsequence-sum/)

[回到目录](../README.md)