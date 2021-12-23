# 1458. max-dot-product-of-two-subsequences | 两个子序列的最大点积

## Question description

<!--If you want to use the English description, use <p>Given two arrays <code>nums1</code>&nbsp;and <code><font face="monospace">nums2</font></code><font face="monospace">.</font></p>

<p>Return the maximum dot product&nbsp;between&nbsp;<strong>non-empty</strong> subsequences of nums1 and nums2 with the same length.</p>

<p>A subsequence of a array is a new array which is formed from the original array by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie,&nbsp;<code>[2,3,5]</code>&nbsp;is a subsequence of&nbsp;<code>[1,2,3,4,5]</code>&nbsp;while <code>[1,5,3]</code>&nbsp;is not).</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [2,1,-2,5], nums2 = [3,0,-6]
<strong>Output:</strong> 18
<strong>Explanation:</strong> Take subsequence [2,-2] from nums1 and subsequence [3,-6] from nums2.
Their dot product is (2*3 + (-2)*(-6)) = 18.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [3,-2], nums2 = [2,-6,7]
<strong>Output:</strong> 21
<strong>Explanation:</strong> Take subsequence [3] from nums1 and subsequence [7] from nums2.
Their dot product is (3*7) = 21.</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [-1,-1], nums2 = [1,1]
<strong>Output:</strong> -1
<strong>Explanation: </strong>Take subsequence [-1] from nums1 and subsequence [1] from nums2.
Their dot product is -1.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums1.length, nums2.length &lt;= 500</code></li>
	<li><code>-1000 &lt;= nums1[i], nums2[i] &lt;= 1000</code></li>
</ul>
 instead-->
<p>给你两个数组&nbsp;<code>nums1</code>&nbsp;和&nbsp;<code>nums2</code>&nbsp;。</p>

<p>请你返回 <code>nums1</code> 和 <code>nums2</code> 中两个长度相同的 <strong>非空</strong> 子序列的最大点积。</p>

<p>数组的非空子序列是通过删除原数组中某些元素（可能一个也不删除）后剩余数字组成的序列，但不能改变数字间相对顺序。比方说，<code>[2,3,5]</code>&nbsp;是&nbsp;<code>[1,2,3,4,5]</code>&nbsp;的一个子序列而&nbsp;<code>[1,5,3]</code>&nbsp;不是。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums1 = [2,1,-2,5], nums2 = [3,0,-6]
<strong>输出：</strong>18
<strong>解释：</strong>从 nums1 中得到子序列 [2,-2] ，从 nums2 中得到子序列 [3,-6] 。
它们的点积为 (2*3 + (-2)*(-6)) = 18 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums1 = [3,-2], nums2 = [2,-6,7]
<strong>输出：</strong>21
<strong>解释：</strong>从 nums1 中得到子序列 [3] ，从 nums2 中得到子序列 [7] 。
它们的点积为 (3*7) = 21 。</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums1 = [-1,-1], nums2 = [1,1]
<strong>输出：</strong>-1
<strong>解释：</strong>从 nums1 中得到子序列 [-1] ，从 nums2 中得到子序列 [1] 。
它们的点积为 -1 。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= nums1.length, nums2.length &lt;= 500</code></li>
	<li><code>-1000 &lt;= nums1[i], nums2[i] &lt;= 100</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>点积：</strong></p>

<pre>
定义 <code><strong>a</strong>&nbsp;= [<em>a</em><sub>1</sub>,&nbsp;<em>a</em><sub>2</sub>,&hellip;,&nbsp;<em>a</em><sub><em>n</em></sub>]</code> 和<strong> <code>b</code></strong><code>&nbsp;= [<em>b</em><sub>1</sub>,&nbsp;<em>b</em><sub>2</sub>,&hellip;,&nbsp;<em>b</em><sub><em>n</em></sub>]</code> 的点积为：

<img alt="\mathbf{a}\cdot \mathbf{b} = \sum_{i=1}^n a_ib_i = a_1b_1 + a_2b_2 + \cdots + a_nb_n " class="tex" src="http://upload.wikimedia.org/math/c/3/2/c329bf86e747d74f55ed2e17c36fd83f.png" />

这里的 <strong>&Sigma;</strong> 指示总和符号。
</pre>




## Solution

Language: **java**  /  Runtime: 11 ms

```java
class Solution {
    public int maxDotProduct(int[] nums1, int[] nums2) {
        int m = nums1.length;
        int n = nums2.length;
        int[][] f = new int[m][n];

        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                int xij = nums1[i] * nums2[j];
                f[i][j] = xij;
                if (i > 0) {
                    f[i][j] = Math.max(f[i][j], f[i - 1][j]);
                }
                if (j > 0) {
                    f[i][j] = Math.max(f[i][j], f[i][j - 1]);
                }
                if (i > 0 && j > 0) {
                    f[i][j] = Math.max(f[i][j], f[i - 1][j - 1] + xij);
                }
            }
        }

        return f[m - 1][n - 1];
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/max-dot-product-of-two-subsequences/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/max-dot-product-of-two-subsequences/description/)

Solution: [LeetCode](https://leetcode.com/articles/max-dot-product-of-two-subsequences/)  /  [LeetCode中国](https://leetcode-cn.com/articles/max-dot-product-of-two-subsequences/)

[回到目录](../README.md)