# 220. contains-duplicate-iii | 存在重复元素 III

## Question description

<!--If you want to use the English description, use <p>Given an integer array <code>nums</code> and two integers <code>k</code> and <code>t</code>, return <code>true</code> if there are <strong>two distinct indices</strong> <code>i</code> and <code>j</code> in the array such that <code>abs(nums[i] - nums[j]) &lt;= t</code> and <code>abs(i - j) &lt;= k</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,2,3,1], k = 3, t = 0
<strong>Output:</strong> true
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [1,0,1,1], k = 1, t = 2
<strong>Output:</strong> true
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [1,5,9,1,5,9], k = 2, t = 3
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
	<li><code>0 &lt;= k &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= t &lt;= 2<sup>31</sup> - 1</code></li>
</ul>
 instead-->
<p>给你一个整数数组 <code>nums</code> 和两个整数 <code>k</code> 和 <code>t</code> 。请你判断是否存在 <b>两个不同下标</b> <code>i</code> 和 <code>j</code>，使得 <code>abs(nums[i] - nums[j]) <= t</code> ，同时又满足 <code>abs(i - j) <= k</code><em> </em>。</p>

<p>如果存在则返回 <code>true</code>，不存在返回 <code>false</code>。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,2,3,1], k<em> </em>= 3, t = 0
<strong>输出：</strong>true</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,0,1,1], k<em> </em>=<em> </em>1, t = 2
<strong>输出：</strong>true</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [1,5,9,1,5,9], k = 2, t = 3
<strong>输出：</strong>false</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= nums.length <= 2 * 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> <= nums[i] <= 2<sup>31</sup> - 1</code></li>
	<li><code>0 <= k <= 10<sup>4</sup></code></li>
	<li><code>0 <= t <= 2<sup>31</sup> - 1</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 34 ms

```java
class Solution {
    public boolean containsNearbyAlmostDuplicate(int[] nums, int k, int t) {
        int n = nums.length;
        TreeSet<Long> set = new TreeSet<Long>();
        for (int i = 0; i < n; i++) {
            Long ceiling = set.ceiling((long) nums[i] - (long) t);
            if (ceiling != null && ceiling <= (long) nums[i] + (long) t) {
                return true;
            }
            set.add((long) nums[i]);
            if (i >= k) {
                set.remove((long) nums[i - k]);
            }
        }
        return false;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/contains-duplicate-iii/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/contains-duplicate-iii/description/)

Solution: [LeetCode](https://leetcode.com/articles/contains-duplicate-iii/)  /  [LeetCode中国](https://leetcode-cn.com/articles/contains-duplicate-iii/)

[回到目录](../README.md)