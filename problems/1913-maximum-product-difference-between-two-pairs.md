# 1913. maximum-product-difference-between-two-pairs | 两个数对之间的最大乘积差

## Question description

<!--If you want to use the English description, use <p>The <strong>product difference</strong> between two pairs <code>(a, b)</code> and <code>(c, d)</code> is defined as <code>(a * b) - (c * d)</code>.</p>

<ul>
	<li>For example, the product difference between <code>(5, 6)</code> and <code>(2, 7)</code> is <code>(5 * 6) - (2 * 7) = 16</code>.</li>
</ul>

<p>Given an integer array <code>nums</code>, choose four <strong>distinct</strong> indices <code>w</code>, <code>x</code>, <code>y</code>, and <code>z</code> such that the <strong>product difference</strong> between pairs <code>(nums[w], nums[x])</code> and <code>(nums[y], nums[z])</code> is <strong>maximized</strong>.</p>

<p>Return <em>the <strong>maximum</strong> such product difference</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [5,6,2,7,4]
<strong>Output:</strong> 34
<strong>Explanation:</strong> We can choose indices 1 and 3 for the first pair (6, 7) and indices 2 and 4 for the second pair (2, 4).
The product difference is (6 * 7) - (2 * 4) = 34.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [4,2,5,9,7,4,8]
<strong>Output:</strong> 64
<strong>Explanation:</strong> We can choose indices 3 and 6 for the first pair (9, 8) and indices 1 and 5 for the second pair (2, 4).
The product difference is (9 * 8) - (2 * 4) = 64.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>4 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul> instead-->
<p>两个数对 <code>(a, b)</code> 和 <code>(c, d)</code> 之间的 <strong>乘积差</strong> 定义为 <code>(a * b) - (c * d)</code> 。</p>

<ul>
	<li>例如，<code>(5, 6)</code> 和 <code>(2, 7)</code> 之间的乘积差是 <code>(5 * 6) - (2 * 7) = 16</code> 。</li>
</ul>

<p>给你一个整数数组 <code>nums</code> ，选出四个 <strong>不同的</strong> 下标 <code>w</code>、<code>x</code>、<code>y</code> 和 <code>z</code> ，使数对 <code>(nums[w], nums[x])</code> 和 <code>(nums[y], nums[z])</code> 之间的 <strong>乘积差</strong> 取到 <strong>最大值</strong> 。</p>

<p>返回以这种方式取得的乘积差中的 <strong>最大值</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [5,6,2,7,4]
<strong>输出：</strong>34
<strong>解释：</strong>可以选出下标为 1 和 3 的元素构成第一个数对 (6, 7) 以及下标 2 和 4 构成第二个数对 (2, 4)
乘积差是 (6 * 7) - (2 * 4) = 34
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [4,2,5,9,7,4,8]
<strong>输出：</strong>64
<strong>解释：</strong>可以选出下标为 3 和 6 的元素构成第一个数对 (9, 8) 以及下标 1 和 5 构成第二个数对 (2, 4)
乘积差是 (9 * 8) - (2 * 4) = 64
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>4 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 8 ms

```java
class Solution {
    public int maxProductDifference(int[] nums) {
        Arrays.sort(nums);
        int n=nums.length;
        return (nums[n-1]*nums[n-2])-(nums[1]*nums[0]);
    }
}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-product-difference-between-two-pairs/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-product-difference-between-two-pairs/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-product-difference-between-two-pairs/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-product-difference-between-two-pairs/)

[回到目录](../README.md)