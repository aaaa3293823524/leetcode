# 1425. constrained-subsequence-sum | 带限制的子序列和

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code> and an integer <code>k</code>, return the maximum sum of a <strong>non-empty</strong> subsequence of that array such that for every two <strong>consecutive</strong> integers in the subsequence, <code>nums[i]</code> and <code>nums[j]</code>, where <code>i &lt; j</code>, the condition <code>j - i &lt;= k</code> is satisfied.</p>

<p>A <em>subsequence</em> of an array is obtained by deleting some number of elements (can be zero) from the array, leaving the remaining elements in their original order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [10,2,-10,5,20], k = 2
<strong>Output:</strong> 37
<b>Explanation:</b> The subsequence is [10, 2, 5, 20].
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [-1,-2,-3], k = 1
<strong>Output:</strong> -1
<b>Explanation:</b> The subsequence must be non-empty, so we choose the largest number.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [10,-2,-10,-5,20], k = 2
<strong>Output:</strong> 23
<b>Explanation:</b> The subsequence is [10, -2, -5, 20].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个整数数组&nbsp;<code>nums</code>&nbsp;和一个整数&nbsp;<code>k</code>&nbsp;，请你返回 <strong>非空</strong>&nbsp;子序列元素和的最大值，子序列需要满足：子序列中每两个 <strong>相邻</strong>&nbsp;的整数&nbsp;<code>nums[i]</code>&nbsp;和&nbsp;<code>nums[j]</code>&nbsp;，它们在原数组中的下标&nbsp;<code>i</code>&nbsp;和&nbsp;<code>j</code>&nbsp;满足&nbsp;<code>i &lt; j</code>&nbsp;且 <code>j - i &lt;= k</code> 。</p>

<p>数组的子序列定义为：将数组中的若干个数字删除（可以删除 0 个数字），剩下的数字按照原本的顺序排布。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [10,2,-10,5,20], k = 2
<strong>输出：</strong>37
<strong>解释：</strong>子序列为 [10, 2, 5, 20] 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [-1,-2,-3], k = 1
<strong>输出：</strong>-1
<strong>解释：</strong>子序列必须是非空的，所以我们选择最大的数字。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>nums = [10,-2,-10,-5,20], k = 2
<strong>输出：</strong>23
<strong>解释：</strong>子序列为 [10, -2, -5, 20] 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= nums.length &lt;= 10^5</code></li>
	<li><code>-10^4&nbsp;&lt;= nums[i] &lt;= 10^4</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 39 ms

```java
class Solution {
    public int constrainedSubsetSum(int[] nums, int k) {
        int n = nums.length;
        int[] f = new int[n];
        f[0] = nums[0];
        Deque<Integer> q = new ArrayDeque<Integer>();
        q.addLast(0);
        int ans = nums[0];
        for (int i = 1; i < n; ++i) {
            // 如果队首的 j 与 i 的差值大于 k，则不满足要求，弹出
            while (!q.isEmpty() && i - q.peekFirst() > k) {
                q.removeFirst();
            }
            // 此时队首的 j 即为最优的 j 值
            f[i] = Math.max(f[q.peekFirst()], 0) + nums[i];
            ans = Math.max(ans, f[i]);
            // 维护队列的单调性，不断从队尾弹出元素
            while (!q.isEmpty() && f[i] >= f[q.peekLast()]) {
                q.removeLast();
            }
            // 将 i 作为之后的新 j 值放入队尾
            q.addLast(i);
        }
        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/constrained-subsequence-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/constrained-subsequence-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/constrained-subsequence-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/constrained-subsequence-sum/)

[回到目录](../README.md)