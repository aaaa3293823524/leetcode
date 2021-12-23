# 485. max-consecutive-ones | 最大连续 1 的个数

## Question description

<!--If you want to use the English description, use <p>Given a binary array <code>nums</code>, return <em>the maximum number of consecutive </em><code>1</code><em>&#39;s in the array</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,1,0,1,1,1]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,0,1,1,0,1]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>nums[i]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>
 instead-->
<p>给定一个二进制数组， 计算其中最大连续 1 的个数。</p>

<p> </p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>[1,1,0,1,1,1]
<strong>输出：</strong>3
<strong>解释：</strong>开头的两位和最后的三位都是连续 1 ，所以最大连续 1 的个数是 3.
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li>输入的数组只包含 <code>0</code> 和 <code>1</code> 。</li>
	<li>输入数组的长度是正整数，且不超过 10,000。</li>
</ul>




## Solution

Language: **java**  /  Runtime: 2 ms

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int maxCount = 0, count = 0;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            if (nums[i] == 1) {
                count++;
            } else {
                maxCount = Math.max(maxCount, count);
                count = 0;
            }
        }
        maxCount = Math.max(maxCount, count);
        return maxCount;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/max-consecutive-ones/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/max-consecutive-ones/description/)

Solution: [LeetCode](https://leetcode.com/articles/max-consecutive-ones/)  /  [LeetCode中国](https://leetcode-cn.com/articles/max-consecutive-ones/)

[回到目录](../README.md)