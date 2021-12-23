# 628. maximum-product-of-three-numbers | 三个数的最大乘积

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code>, <em>find three numbers whose product is maximum and return the maximum product</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3]
<strong>Output:</strong> 6
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3,4]
<strong>Output:</strong> 24
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [-1,-2,-3]
<strong>Output:</strong> -6
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= nums.length &lt;=&nbsp;10<sup>4</sup></code></li>
	<li><code>-1000 &lt;= nums[i] &lt;= 1000</code></li>
</ul>
 instead-->
<p>给你一个整型数组 <code>nums</code> ，在数组中找出由三个数组成的最大乘积，并输出这个乘积。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,3]
<strong>输出：</strong>6
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,3,4]
<strong>输出：</strong>24
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [-1,-2,-3]
<strong>输出：</strong>-6
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>3 <= nums.length <= 10<sup>4</sup></code></li>
	<li><code>-1000 <= nums[i] <= 1000</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 6 ms

```java
class Solution {
    public int maximumProduct(int[] nums) {
        int max1 = -1001, max2 = -1001, max3 = -1001;
        int min1 = 1001, min2 = 1001;
        for (int num : nums) {
            if (num > max1) {
                max3=max2;
                max2=max1;
                max1=num;
            } else if (num > max2) {
                max3=max2;
                max2=num;
            } else if (num > max3) {
                max3=num;
            }

            if (num < min1) {
                min2=min1;
                min1 = num;
            } else if (num < min2) {
               min2=num;
            }
        }
        return Math.max(max2 * max3 * max1, min1 * min2 * max1) ;
    }


}
```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-product-of-three-numbers/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-product-of-three-numbers/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-product-of-three-numbers/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-product-of-three-numbers/)

[回到目录](../README.md)