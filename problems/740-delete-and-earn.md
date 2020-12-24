# 740. delete-and-earn | 删除与获得点数

## Question description

<!--If you want to use the English description, use <p>Given an array <code>nums</code> of integers, you can perform operations on the array.</p>

<p>In each operation, you pick any <code>nums[i]</code> and delete it to earn <code>nums[i]</code> points. After, you must delete <b>every</b> element equal to <code>nums[i] - 1</code> or <code>nums[i] + 1</code>.</p>

<p>You start with 0 points. Return the maximum number of points you can earn by applying such operations.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> nums = [3, 4, 2]
<b>Output:</b> 6
<b>Explanation:</b> 
Delete 4 to earn 4 points, consequently 3 is also deleted.
Then, delete 2 to earn 2 points. 6 total points are earned.
</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> nums = [2, 2, 3, 3, 3, 4]
<b>Output:</b> 9
<b>Explanation:</b> 
Delete 3 to earn 3 points, deleting both 2&#39;s and the 4.
Then, delete 3 again to earn 3 points, and 3 again to earn 3 points.
9 total points are earned.
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ul>
	<li>The length of <code>nums</code> is at most <code>20000</code>.</li>
	<li>Each element <code>nums[i]</code> is an integer in the range <code>[1, 10000]</code>.</li>
</ul>

<p>&nbsp;</p>
 instead-->
<p>给定一个整数数组&nbsp;<code>nums</code>&nbsp;，你可以对它进行一些操作。</p>

<p>每次操作中，选择任意一个&nbsp;<code>nums[i]</code>&nbsp;，删除它并获得&nbsp;<code>nums[i]</code>&nbsp;的点数。之后，你必须删除<strong>每个</strong>等于&nbsp;<code>nums[i] - 1</code>&nbsp;或&nbsp;<code>nums[i] + 1</code>&nbsp;的元素。</p>

<p>开始你拥有 0 个点数。返回你能通过这些操作获得的最大点数。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> nums = [3, 4, 2]
<strong>输出:</strong> 6
<strong>解释:</strong> 
删除 4 来获得 4 个点数，因此 3 也被删除。
之后，删除 2 来获得 2 个点数。总共获得 6 个点数。
</pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>
<strong>输入:</strong> nums = [2, 2, 3, 3, 3, 4]
<strong>输出:</strong> 9
<strong>解释:</strong> 
删除 3 来获得 3 个点数，接着要删除两个 2 和 4 。
之后，再次删除 3 获得 3 个点数，再次删除 3 获得 3 个点数。
总共获得 9 个点数。
</pre>

<p><strong>注意:</strong></p>

<ul>
	<li><code>nums</code>的长度最大为<code>20000</code>。</li>
	<li>每个整数<code>nums[i]</code>的大小都在<code>[1, 10000]</code>范围内。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public int deleteAndEarn(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        } else if (nums.length == 1) {
            return nums[0];
        }
        int len = nums.length;
        int max = nums[0];
        for (int i = 0; i < len; ++i) {
           max = Math.max(max, nums[i]);
        }
//      构造一个新的数组all
        int[] all = new int[max + 1];
        for (int item : nums) {
            all[item] ++;
        }
        int[] dp = new int[max + 1];
        dp[1] = all[1] * 1;
        dp[2] = Math.max(dp[1], all[2] * 2);
//      动态规划求解
        for (int i = 2; i <= max; ++i) {
            dp[i] = Math.max(dp[i - 1], dp[i - 2] + i * all[i]);
        }
        return dp[max];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/delete-and-earn/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/delete-and-earn/description/)

Solution: [LeetCode](https://leetcode.com/articles/delete-and-earn/)  /  [LeetCode中国](https://leetcode-cn.com/articles/delete-and-earn/)

[回到目录](../README.md)