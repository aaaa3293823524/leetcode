# 1043. partition-array-for-maximum-sum | 分隔数组以得到最大和

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>arr</code>, partition the array into (contiguous) subarrays of length <strong>at most</strong> <code>k</code>. After partitioning, each subarray has their values changed to become the maximum value of that subarray.</p>

<p>Return <em>the largest sum of the given array after partitioning. Test cases are generated so that the answer fits in a <strong>32-bit</strong> integer.</em></p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,15,7,9,2,5,10], k = 3
<strong>Output:</strong> 84
<strong>Explanation:</strong> arr becomes [15,15,15,9,10,10,10]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> arr = [1,4,1,5,7,3,6,1,9,9,3], k = 4
<strong>Output:</strong> 83
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> arr = [1], k = 1
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 500</code></li>
	<li><code>0 &lt;= arr[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= k &lt;= arr.length</code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>arr</code>，请你将该数组分隔为长度最多为 k 的一些（连续）子数组。分隔完成后，每个子数组的中的所有值都会变为该子数组中的最大值。</p>

<p>返回将数组分隔变换后能够得到的元素最大和。</p>

<p> </p>

<p><strong>注意，</strong>原数组和分隔后的数组对应顺序应当一致，也就是说，你只能选择分隔数组的位置而不能调整数组中的顺序。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>arr = [1,15,7,9,2,5,10], k = 3
<strong>输出：</strong>84
<strong>解释：</strong>
因为 k=3 可以分隔成 [1,15,7] [9] [2,5,10]，结果为 [15,15,15,9,10,10,10]，和为 84，是该数组所有分隔变换后元素总和最大的。
若是分隔成 [1] [15,7,9] [2,5,10]，结果就是 [1, 15, 15, 15, 10, 10, 10] 但这种分隔方式的元素总和（76）小于上一种。 </pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>arr = [1,4,1,5,7,3,6,1,9,9,3], k = 4
<strong>输出：</strong>83
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>arr = [1], k = 1
<strong>输出：</strong>1
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= arr.length <= 500</code></li>
	<li><code>0 <= arr[i] <= 10<sup>9</sup></code></li>
	<li><code>1 <= k <= arr.length</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 44 ms

```java
class Solution {
    long res = 0;

    public int maxSumAfterPartitioning(int[] arr, int k) {
        int length = arr.length;
        int[] dp = new int[length];
        for (int i = 1; i <= k; i++) {
            dp[i - 1] = getMaxValue(arr, 0, i - 1) * i;
        }
        for (int i = k; i < length; i++) {
            for (int j = 1; j <= k; j++) {
                dp[i] = Math.max(dp[i - j] + getMaxValue(arr, i - j + 1, i) * j, dp[i]);
            }
        }

        return dp[length - 1];
    }
    
    private int getMaxValue(int[] arr, int start, int end) {
        int res = 0;
        for (int i = start; i <= end; i++) {
            res = Math.max(res, arr[i]);
        }
        return res;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/partition-array-for-maximum-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/partition-array-for-maximum-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/partition-array-for-maximum-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/partition-array-for-maximum-sum/)

[回到目录](../README.md)