# 410. split-array-largest-sum | 分割数组的最大值

## Question description

<!--If you want to use the English description, use <p>Given an array <code>nums</code> which consists of non-negative integers and an integer <code>m</code>, you can split the array into <code>m</code> non-empty continuous subarrays.</p>

<p>Write an algorithm to minimize the largest sum among these <code>m</code> subarrays.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [7,2,5,10,8], m = 2
<strong>Output:</strong> 18
<strong>Explanation:</strong>
There are four ways to split nums into two subarrays.
The best way is to split it into [7,2,5] and [10,8],
where the largest sum among the two subarrays is only 18.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,2,3,4,5], m = 2
<strong>Output:</strong> 9
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,4,4], m = 3
<strong>Output:</strong> 4
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 1000</code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>6</sup></code></li>
	<li><code>1 &lt;= m &lt;= min(50, nums.length)</code></li>
</ul>
 instead-->
<p>给定一个非负整数数组 <code>nums</code> 和一个整数 <code>m</code> ，你需要将这个数组分成 <code>m</code><em> </em>个非空的连续子数组。</p>

<p>设计一个算法使得这 <code>m</code><em> </em>个子数组各自和的最大值最小。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [7,2,5,10,8], m = 2
<strong>输出：</strong>18
<strong>解释：</strong>
一共有四种方法将 nums 分割为 2 个子数组。 其中最好的方式是将其分为 [7,2,5] 和 [10,8] 。
因为此时这两个子数组各自的和的最大值为18，在所有情况中最小。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,3,4,5], m = 2
<strong>输出：</strong>9
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,4,4], m = 3
<strong>输出：</strong>4
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 1000</code></li>
	<li><code>0 <= nums[i] <= 10<sup>6</sup></code></li>
	<li><code>1 <= m <= min(50, nums.length)</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int splitArray(int[] nums, int m) {
        int left = 0, right = 0;
        for (int i = 0; i < nums.length; i++) {
            right += nums[i];
            if (left < nums[i]) {
                left = nums[i];
            }
        }
        while (left < right) {
            int mid = (right - left) / 2 + left;
            if (check(nums, mid, m)) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }

    public boolean check(int[] nums, int x, int m) {
        int sum = 0;
        int cnt = 1;
        for (int i = 0; i < nums.length; i++) {
            if (sum + nums[i] > x) {
                cnt++;
                sum = nums[i];
            } else {
                sum += nums[i];
            }
        }
        return cnt <= m;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/split-array-largest-sum/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/split-array-largest-sum/description/)

Solution: [LeetCode](https://leetcode.com/articles/split-array-largest-sum/)  /  [LeetCode中国](https://leetcode-cn.com/articles/split-array-largest-sum/)

[回到目录](../README.md)