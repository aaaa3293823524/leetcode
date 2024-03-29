﻿# 1031. maximum-sum-of-two-non-overlapping-subarrays | 两个非重叠子数组的最大和

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code> and two integers <code>firstLen</code> and <code>secondLen</code>, return <em>the maximum sum of elements in two non-overlapping <strong>subarrays</strong> with lengths </em><code>firstLen</code><em> and </em><code>secondLen</code>.</p>

<p>The array with length <code>firstLen</code> could occur before or after the array with length <code>secondLen</code>, but they have to be non-overlapping.</p>

<p>A <strong>subarray</strong> is a <strong>contiguous</strong> part of an array.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,6,5,2,2,5,1,9,4], firstLen = 1, secondLen = 2
<strong>Output:</strong> 20
<strong>Explanation:</strong> One choice of subarrays is [9] with length 1, and [6,5] with length 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [3,8,1,3,2,1,8,9,0], firstLen = 3, secondLen = 2
<strong>Output:</strong> 29
<strong>Explanation:</strong> One choice of subarrays is [3,8,1] with length 3, and [8,9] with length 2.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,1,5,6,0,9,5,0,3,8], firstLen = 4, secondLen = 3
<strong>Output:</strong> 31
<strong>Explanation:</strong> One choice of subarrays is [5,6,0,9] with length 4, and [3,8] with length 3.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= firstLen, secondLen &lt;= 1000</code></li>
	<li><code>2 &lt;= firstLen + secondLen &lt;= 1000</code></li>
	<li><code>firstLen + secondLen &lt;= nums.length &lt;= 1000</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 1000</code></li>
</ul>
 instead-->
<p>给出非负整数数组 <code>A</code> ，返回两个非重叠（连续）子数组中元素的最大和，子数组的长度分别为 <code>L</code> 和 <code>M</code>。（这里需要澄清的是，长为 L 的子数组可以出现在长为 M 的子数组之前或之后。）</p>

<p>从形式上看，返回最大的 <code>V</code>，而 <code>V = (A[i] + A[i+1] + ... + A[i+L-1]) + (A[j] + A[j+1] + ... + A[j+M-1])</code> 并满足下列条件之一：</p>

<p>&nbsp;</p>

<ul>
	<li><code>0 &lt;= i &lt; i + L - 1 &lt; j &lt; j + M - 1 &lt; A.length</code>, <strong>或</strong></li>
	<li><code>0 &lt;= j &lt; j + M - 1 &lt; i &lt; i + L - 1 &lt; A.length</code>.</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>A = [0,6,5,2,2,5,1,9,4], L = 1, M = 2
<strong>输出：</strong>20
<strong>解释：</strong>子数组的一种选择中，[9] 长度为 1，[6,5] 长度为 2。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>A = [3,8,1,3,2,1,8,9,0], L = 3, M = 2
<strong>输出：</strong>29
<strong>解释：</strong>子数组的一种选择中，[3,8,1] 长度为 3，[8,9] 长度为 2。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>A = [2,1,5,6,0,9,5,0,3,8], L = 4, M = 3
<strong>输出：</strong>31
<strong>解释：</strong>子数组的一种选择中，[5,6,0,9] 长度为 4，[0,3,8] 长度为 3。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>L &gt;= 1</code></li>
	<li><code>M &gt;= 1</code></li>
	<li><code>L + M &lt;= A.length &lt;= 1000</code></li>
	<li><code>0 &lt;= A[i] &lt;= 1000</code></li>
</ol>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public int maxSumTwoNoOverlap(int[] nums, int f, int s) {
        int n = nums.length;
        int[] sum = new int[n+1];
        for (int i = 0;i < n;i++) sum[i+1] = sum[i] + nums[i];
        if (f > s) {
            int t = f; f = s; s = t;
        }
        int[][] dp = new int[n+1][2];
        int max = 0;
        for (int i = f;i <= n;i++) {
            int s1 = sum[i] - sum[i-f];
            dp[i][0] = Math.max(dp[i-1][0], s1);
            max = Math.max(max, s1 + dp[i-f][1]);
            if (i >= s) {
                int s2 = sum[i] - sum[i-s];
                dp[i][1] = Math.max(dp[i-1][1], s2);
                max = Math.max(max, s2 + dp[i-s][0]);
            }
        }
        return max;
    }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-sum-of-two-non-overlapping-subarrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-sum-of-two-non-overlapping-subarrays/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-sum-of-two-non-overlapping-subarrays/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-sum-of-two-non-overlapping-subarrays/)

[回到目录](../README.md)