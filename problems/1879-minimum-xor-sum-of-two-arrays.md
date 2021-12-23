# 1879. minimum-xor-sum-of-two-arrays | 两个数组最小的异或值之和

## Question description

<!--If you want to use the English description, use <p>You are given two integer arrays <code>nums1</code> and <code>nums2</code> of length <code>n</code>.</p>

<p>The <strong>XOR sum</strong> of the two integer arrays is <code>(nums1[0] XOR nums2[0]) + (nums1[1] XOR nums2[1]) + ... + (nums1[n - 1] XOR nums2[n - 1])</code> (<strong>0-indexed</strong>).</p>

<ul>
	<li>For example, the <strong>XOR sum</strong> of <code>[1,2,3]</code> and <code>[3,2,1]</code> is equal to <code>(1 XOR 3) + (2 XOR 2) + (3 XOR 1) = 2 + 0 + 2 = 4</code>.</li>
</ul>

<p>Rearrange the elements of <code>nums2</code> such that the resulting <strong>XOR sum</strong> is <b>minimized</b>.</p>

<p>Return <em>the <strong>XOR sum</strong> after the rearrangement</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,2], nums2 = [2,3]
<strong>Output:</strong> 2
<b>Explanation:</b> Rearrange <code>nums2</code> so that it becomes <code>[3,2]</code>.
The XOR sum is (1 XOR 3) + (2 XOR 2) = 2 + 0 = 2.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums1 = [1,0,3], nums2 = [5,3,4]
<strong>Output:</strong> 8
<b>Explanation:</b> Rearrange <code>nums2</code> so that it becomes <code>[5,4,3]</code>. 
The XOR sum is (1 XOR 5) + (0 XOR 4) + (3 XOR 3) = 4 + 4 + 0 = 8.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums1.length</code></li>
	<li><code>n == nums2.length</code></li>
	<li><code>1 &lt;= n &lt;= 14</code></li>
	<li><code>0 &lt;= nums1[i], nums2[i] &lt;= 10<sup>7</sup></code></li>
</ul>
 instead-->
<p>给你两个整数数组 <code>nums1</code> 和 <code>nums2</code> ，它们长度都为 <code>n</code> 。</p>

<p>两个数组的 <strong>异或值之和</strong> 为 <code>(nums1[0] XOR nums2[0]) + (nums1[1] XOR nums2[1]) + ... + (nums1[n - 1] XOR nums2[n - 1])</code> （<strong>下标从 0 开始</strong>）。</p>

<ul>
	<li>比方说，<code>[1,2,3]</code> 和 <code>[3,2,1]</code> 的 <strong>异或值之和</strong> 等于 <code>(1 XOR 3) + (2 XOR 2) + (3 XOR 1) = 2 + 0 + 2 = 4</code> 。</li>
</ul>

<p>请你将 <code>nums2</code> 中的元素重新排列，使得 <strong>异或值之和</strong> <strong>最小</strong> 。</p>

<p>请你返回重新排列之后的 <strong>异或值之和</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>nums1 = [1,2], nums2 = [2,3]
<b>输出：</b>2
<b>解释：</b>将 <code>nums2</code> 重新排列得到 <code>[3,2] 。</code>
异或值之和为 (1 XOR 3) + (2 XOR 2) = 2 + 0 = 2 。</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>nums1 = [1,0,3], nums2 = [5,3,4]
<b>输出：</b>8
<b>解释：</b>将 <code>nums2 重新排列得到</code> <code>[5,4,3] 。</code>
异或值之和为 (1 XOR 5) + (0 XOR 4) + (3 XOR 3) = 4 + 4 + 0 = 8 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == nums1.length</code></li>
	<li><code>n == nums2.length</code></li>
	<li><code>1 &lt;= n &lt;= 14</code></li>
	<li><code>0 &lt;= nums1[i], nums2[i] &lt;= 10<sup>7</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 15 ms

```java
class Solution {
    public int minimumXORSum(int[] nums1, int[] nums2) {
        int n = nums1.length, range = 1 << n;
        int[] dp = new int[range];//若i的二进制表示中1的个数为num, 1的位置为k1,k2,...,knum, dp[i]表示nums1的前num个数和nums2第k1,k2,...,knum个数的最小异或值之和
        Arrays.fill(dp, Integer.MAX_VALUE);
        dp[0] = 0;
        for (int i = 0; i < range; i++) {
            for (int j = 0; j < n; j++) {//遍历i的各个二进制位
                if (((i >> j) & 1) == 1)//i的第j位为1
                    dp[i] = Math.min(dp[i], dp[i ^ (1 << j)] + (nums1[Integer.bitCount(i) - 1] ^ nums2[j]));//尝试选取nums1[num]和nums2[j]进行异或更新dp[i]
            }
        }
        return dp[range - 1];//答案为dp[111...1](n个1)
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/minimum-xor-sum-of-two-arrays/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/minimum-xor-sum-of-two-arrays/description/)

Solution: [LeetCode](https://leetcode.com/articles/minimum-xor-sum-of-two-arrays/)  /  [LeetCode中国](https://leetcode-cn.com/articles/minimum-xor-sum-of-two-arrays/)

[回到目录](../README.md)