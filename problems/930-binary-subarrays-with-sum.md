# 930. binary-subarrays-with-sum | 和相同的二元子数组

## Question description

<!--If you want to use the English description, use <p>Given a binary array <code>nums</code> and an integer <code>goal</code>, return <em>the number of non-empty <strong>subarrays</strong> with a sum</em> <code>goal</code>.</p>

<p>A <strong>subarray</strong> is a contiguous part of the array.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,0,1,0,1], goal = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> The 4 subarrays are bolded and underlined below:
[<u><strong>1,0,1</strong></u>,0,1]
[<u><strong>1,0,1,0</strong></u>,1]
[1,<u><strong>0,1,0,1</strong></u>]
[1,0,<u><strong>1,0,1</strong></u>]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [0,0,0,0,0], goal = 0
<strong>Output:</strong> 15
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>nums[i]</code> is either <code>0</code> or <code>1</code>.</li>
	<li><code>0 &lt;= goal &lt;= nums.length</code></li>
</ul> instead-->
<p>给你一个二元数组 <code>nums</code> ，和一个整数 <code>goal</code> ，请你统计并返回有多少个和为 <code>goal</code> 的<strong> 非空</strong> 子数组。</p>

<p><strong>子数组</strong> 是数组的一段连续部分。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,0,1,0,1], goal = 2
<strong>输出：</strong>4
<strong>解释：</strong>
有 4 个满足题目要求的子数组：[1,0,1]、[1,0,1,0]、[0,1,0,1]、[1,0,1]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [0,0,0,0,0], goal = 0
<strong>输出：</strong>15
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 3 * 10<sup>4</sup></code></li>
	<li><code>nums[i]</code> 不是 <code>0</code> 就是 <code>1</code></li>
	<li><code>0 <= goal <= nums.length</code></li>
</ul>


## Note

前缀和   P[i] = A[0] + A[1] + ... + A[i - 1]



这样就可以通过 P[j + 1] - P[i] = A[i] + A[i + 1] + ... + A[j] 快速计算出 A[i..j] 的和。



我们可以对数组 P 进行一次线性扫描，当扫描到 P[j] 时，我们需要得到的是满足 P[j] = P[i] + S 且 i < j 的 i 的数目，使用计数器（map 或 dict）可以满足要求





3指针


## Solution

Language: **java**  /  Runtime: 22 ms

```java
class Solution {
    public int numSubarraysWithSum(int[] A, int S) {
        int N = A.length;
        int[] P = new int[N + 1];
        for (int i = 0; i < N; ++i)
            P[i+1] = P[i] + A[i];

        Map<Integer, Integer> count = new HashMap();
        int ans = 0;
        for (int x: P) {
            ans += count.getOrDefault(x, 0);
            count.put(x+S, count.getOrDefault(x+S, 0) + 1);
        }

        return ans;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/binary-subarrays-with-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/binary-subarrays-with-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/binary-subarrays-with-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/binary-subarrays-with-sum/)

[回到目录](../README.md)