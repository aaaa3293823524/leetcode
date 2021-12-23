# 剑指 Offer II 010. QTMn0o | 和为 k 的子数组

## Question description

<!--If you want to use the English description, use <p>English description is not available for the problem. Please switch to Chinese.</p>
 instead-->
<p>给定一个整数数组和一个整数&nbsp;<code>k</code><strong> ，</strong>请找到该数组中和为&nbsp;<code>k</code><strong>&nbsp;</strong>的连续子数组的个数。</p>

<p>&nbsp;</p>

<p><strong>示例 1 :</strong></p>

<pre>
<strong>输入:</strong>nums = [1,1,1], k = 2
<strong>输出:</strong> 2
<strong>解释:</strong> 此题 [1,1] 与 [1,1] 为两种不同的情况
</pre>

<p><strong>示例 2&nbsp;:</strong></p>

<pre>
<strong>输入:</strong>nums = [1,2,3], k = 3
<strong>输出:</strong> 2
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
	<li>
	<p><code>-10<sup>7</sup>&nbsp;&lt;= k &lt;= 10<sup>7</sup></code></p>
	</li>
</ul>

<p>&nbsp;</p>

<p>注意：本题与主站 560&nbsp;题相同：&nbsp;<a href="https://leetcode-cn.com/problems/subarray-sum-equals-k/">https://leetcode-cn.com/problems/subarray-sum-equals-k/</a></p>




## Solution

Language: **java**  /  Runtime: 23 ms

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int pre_sum = 0;
        int ret = 0;
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        for (int i : nums) {
            pre_sum += i;
            ret += map.getOrDefault(pre_sum - k, 0);
            map.put(pre_sum, map.getOrDefault(pre_sum, 0) + 1);
        }
        return ret;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/QTMn0o/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/QTMn0o/description/)

Solution: [LeetCode](https://leetcode.com/articles/QTMn0o/)  /  [LeetCode中国](https://leetcode-cn.com/articles/QTMn0o/)

[回到目录](../README.md)