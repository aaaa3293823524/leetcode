# 1749. maximum-absolute-sum-of-any-subarray | 任意子数组和的绝对值的最大值

## Question description

<!--If you want to use the English description, use <p>You are given an integer array <code>nums</code>. The <strong>absolute sum</strong> of a subarray <code>[nums<sub>l</sub>, nums<sub>l+1</sub>, ..., nums<sub>r-1</sub>, nums<sub>r</sub>]</code> is <code>abs(nums<sub>l</sub> + nums<sub>l+1</sub> + ... + nums<sub>r-1</sub> + nums<sub>r</sub>)</code>.</p>

<p>Return <em>the <strong>maximum</strong> absolute sum of any <strong>(possibly empty)</strong> subarray of </em><code>nums</code>.</p>

<p>Note that <code>abs(x)</code> is defined as follows:</p>

<ul>
	<li>If <code>x</code> is a negative integer, then <code>abs(x) = -x</code>.</li>
	<li>If <code>x</code> is a non-negative integer, then <code>abs(x) = x</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1,-3,2,3,-4]
<strong>Output:</strong> 5
<strong>Explanation:</strong> The subarray [2,3] has absolute sum = abs(2+3) = abs(5) = 5.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,-5,1,-4,3,-2]
<strong>Output:</strong> 8
<strong>Explanation:</strong> The subarray [-5,1,-4] has absolute sum = abs(-5+1-4) = abs(-8) = 8.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>nums</code> 。一个子数组 <code>[nums<sub>l</sub>, nums<sub>l+1</sub>, ..., nums<sub>r-1</sub>, nums<sub>r</sub>]</code> 的 <strong>和的绝对值</strong> 为 <code>abs(nums<sub>l</sub> + nums<sub>l+1</sub> + ... + nums<sub>r-1</sub> + nums<sub>r</sub>)</code> 。</p>

<p>请你找出 <code>nums</code> 中 <strong>和的绝对值</strong> 最大的任意子数组（<b>可能为空</b>），并返回该 <strong>最大值</strong> 。</p>

<p><code>abs(x)</code> 定义如下：</p>

<ul>
	<li>如果 <code>x</code> 是负整数，那么 <code>abs(x) = -x</code> 。</li>
	<li>如果 <code>x</code> 是非负整数，那么 <code>abs(x) = x</code> 。</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>nums = [1,-3,2,3,-4]
<b>输出：</b>5
<b>解释：</b>子数组 [2,3] 和的绝对值最大，为 abs(2+3) = abs(5) = 5 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>nums = [2,-5,1,-4,3,-2]
<b>输出：</b>8
<b>解释：</b>子数组 [-5,1,-4] 和的绝对值最大，为 abs(-5+1-4) = abs(-8) = 8 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= nums.length <= 10<sup>5</sup></code></li>
	<li><code>-10<sup>4</sup> <= nums[i] <= 10<sup>4</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 3 ms

```java
class Solution {
    public int maxAbsoluteSum(int[] nums) {
        int length = nums.length;
        if (length < 2)return Math.abs(nums[0]);
        int max = nums[0],min = nums[0];
        for (int i = 1; i < nums.length; i++) {
            nums[i] += nums[i - 1];
            if (nums[i] > max){
                max = nums[i];
            }else if (nums[i] < min){
                min = nums[i];
            }
        }
        return Math.max(max - min,Math.max(Math.abs(min),Math.abs(max)));
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-absolute-sum-of-any-subarray/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-absolute-sum-of-any-subarray/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-absolute-sum-of-any-subarray/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-absolute-sum-of-any-subarray/)

[回到目录](../README.md)