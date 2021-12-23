# 2025. maximum-number-of-ways-to-partition-an-array | 分割数组的最多方案数

## Question description

<!--If you want to use the English description, use <p>You are given a <strong>0-indexed</strong> integer array <code>nums</code> of length <code>n</code>. The number of ways to <strong>partition</strong> <code>nums</code> is the number of <code>pivot</code> indices that satisfy both conditions:</p>

<ul>
	<li><code>1 &lt;= pivot &lt; n</code></li>
	<li><code>nums[0] + nums[1] + ... + nums[pivot - 1] == nums[pivot] + nums[pivot + 1] + ... + nums[n - 1]</code></li>
</ul>

<p>You are also given an integer <code>k</code>. You can choose to change the value of <strong>one</strong> element of <code>nums</code> to <code>k</code>, or to leave the array <strong>unchanged</strong>.</p>

<p>Return <em>the <strong>maximum</strong> possible number of ways to <strong>partition</strong> </em><code>nums</code><em> to satisfy both conditions after changing <strong>at most</strong> one element</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,-1,2], k = 3
<strong>Output:</strong> 1
<strong>Explanation:</strong> One optimal approach is to change nums[0] to k. The array becomes [<strong><u>3</u></strong>,-1,2].
There is one way to partition the array:
- For pivot = 2, we have the partition [3,-1 | 2]: 3 + -1 == 2.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,0,0], k = 1
<strong>Output:</strong> 2
<strong>Explanation:</strong> The optimal approach is to leave the array unchanged.
There are two ways to partition the array:
- For pivot = 1, we have the partition [0 | 0,0]: 0 == 0 + 0.
- For pivot = 2, we have the partition [0,0 | 0]: 0 + 0 == 0.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [22,4,-25,-20,-15,15,-16,7,19,-10,0,-13,-14], k = -33
<strong>Output:</strong> 4
<strong>Explanation:</strong> One optimal approach is to change nums[2] to k. The array becomes [22,4,<u><strong>-33</strong></u>,-20,-15,15,-16,7,19,-10,0,-13,-14].
There are four ways to partition the array.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>2 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>5</sup> &lt;= k, nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>
 instead-->
<p>给你一个下标从 <strong>0</strong>&nbsp;开始且长度为 <code>n</code>&nbsp;的整数数组&nbsp;<code>nums</code>&nbsp;。<strong>分割</strong>&nbsp;数组 <code>nums</code>&nbsp;的方案数定义为符合以下两个条件的 <code>pivot</code>&nbsp;数目：</p>

<ul>
	<li><code>1 &lt;= pivot &lt; n</code></li>
	<li><code>nums[0] + nums[1] + ... + nums[pivot - 1] == nums[pivot] + nums[pivot + 1] + ... + nums[n - 1]</code></li>
</ul>

<p>同时给你一个整数&nbsp;<code>k</code>&nbsp;。你可以将&nbsp;<code>nums</code>&nbsp;中&nbsp;<strong>一个</strong>&nbsp;元素变为&nbsp;<code>k</code>&nbsp;或&nbsp;<strong>不改变</strong>&nbsp;数组。</p>

<p>请你返回在 <strong>至多</strong>&nbsp;改变一个元素的前提下，<strong>最多</strong>&nbsp;有多少种方法 <strong>分割</strong>&nbsp;<code>nums</code>&nbsp;使得上述两个条件都满足。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>nums = [2,-1,2], k = 3
<b>输出：</b>1
<b>解释：</b>一个最优的方案是将 nums[0] 改为 k&nbsp;。数组变为 [<em><strong>3</strong></em>,-1,2] 。
有一种方法分割数组：
- pivot = 2 ，我们有分割 [3,-1 | 2]：3 + -1 == 2 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>nums = [0,0,0], k = 1
<b>输出：</b>2
<b>解释：</b>一个最优的方案是不改动数组。
有两种方法分割数组：
- pivot = 1 ，我们有分割 [0 | 0,0]：0 == 0 + 0 。
- pivot = 2 ，我们有分割 [0,0 | 0]: 0 + 0 == 0 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>nums = [22,4,-25,-20,-15,15,-16,7,19,-10,0,-13,-14], k = -33
<b>输出：</b>4
<b>解释：</b>一个最优的方案是将 nums[2] 改为 k 。数组变为 [22,4,<em><strong>-33</strong></em>,-20,-15,15,-16,7,19,-10,0,-13,-14] 。
有四种方法分割数组。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>2 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>5</sup> &lt;= k, nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 189 ms

```java
class Solution {
    public int waysToPartition(int[] nums, int k) {
        int n = nums.length;
        int[] preSum = new int[n + 1];
        Map<Integer, Integer> m1 = new HashMap<>();
        Map<Integer, Integer> m2 = new HashMap<>();
        for (int i = 1; i <= n; i++) {
            preSum[i] = nums[i - 1] + preSum[i - 1];
            // 一开始除了最后一个前缀和，其余均在m2中
            if (i != n) m2.put(preSum[i], m2.getOrDefault(preSum[i], 0) + 1);
        }
        int ans = 0;
        if (preSum[n] % 2 == 0) {
            // 若一个元素都不修改
            ans = m2.getOrDefault(preSum[n] / 2, 0);
        }
        for (int i = 0; i < n; i++) {
            // 修改下标为i的元素变成k
            int change = k - nums[i];
            // 所有元素总和的变化量也是change
            int pn = preSum[n] + change;
            if (pn % 2 == 0) {
                // 在m1中我们要找的目标是 target1 = 总和/2 的数量
                int t1 = pn / 2;
                // 在m2中我们要找的目标是 target2 = target1 - change 的数量
                int t2 = t1 - change;
                int found = m1.getOrDefault(t1, 0) + m2.getOrDefault(t2, 0);
                ans = Math.max(ans, found);
            }
            // 不断减少m2中的计数，增加m1对应的计数
            if (i != n - 1) {
                m1.put(preSum[i + 1], m1.getOrDefault(preSum[i + 1], 0) + 1);
                int tmp = m2.get(preSum[i + 1]);
                if (tmp == 1) {
                    m2.remove(preSum[i + 1]);
                } else {
                    m2.put(preSum[i + 1], tmp - 1);
                }
            }
        }
        return ans;
    }

}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-number-of-ways-to-partition-an-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-number-of-ways-to-partition-an-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-number-of-ways-to-partition-an-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-number-of-ways-to-partition-an-array/)

[回到目录](../README.md)