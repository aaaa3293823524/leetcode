# 2016. maximum-difference-between-increasing-elements | 增量元素之间的最大差值

## Question description

<!--If you want to use the English description, use <p>Given a <strong>0-indexed</strong> integer array <code>nums</code> of size <code>n</code>, find the <strong>maximum difference</strong> between <code>nums[i]</code> and <code>nums[j]</code> (i.e., <code>nums[j] - nums[i]</code>), such that <code>0 &lt;= i &lt; j &lt; n</code> and <code>nums[i] &lt; nums[j]</code>.</p>

<p>Return <em>the <strong>maximum difference</strong>. </em>If no such <code>i</code> and <code>j</code> exists, return <code>-1</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [7,<strong><u>1</u></strong>,<strong><u>5</u></strong>,4]
<strong>Output:</strong> 4
<strong>Explanation:</strong>
The maximum difference occurs with i = 1 and j = 2, nums[j] - nums[i] = 5 - 1 = 4.
Note that with i = 1 and j = 0, the difference nums[j] - nums[i] = 7 - 1 = 6, but i &gt; j, so it is not valid.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [9,4,3,2]
<strong>Output:</strong> -1
<strong>Explanation:</strong>
There is no i and j such that i &lt; j and nums[i] &lt; nums[j].
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [<strong><u>1</u></strong>,5,2,<strong><u>10</u></strong>]
<strong>Output:</strong> 9
<strong>Explanation:</strong>
The maximum difference occurs with i = 0 and j = 3, nums[j] - nums[i] = 10 - 1 = 9.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>2 &lt;= n &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>
 instead-->
<p>给你一个下标从 <strong>0</strong> 开始的整数数组 <code>nums</code> ，该数组的大小为 <code>n</code> ，请你计算 <code>nums[j] - nums[i]</code> 能求得的 <strong>最大差值 </strong>，其中 <code>0 &lt;= i &lt; j &lt; n</code> 且 <code>nums[i] &lt; nums[j]</code> 。</p>

<p>返回 <strong>最大差值</strong> 。如果不存在满足要求的 <code>i</code> 和 <code>j</code> ，返回 <code>-1</code> 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>nums = [7,<em><strong>1</strong></em>,<em><strong>5</strong></em>,4]
<strong>输出：</strong>4
<strong>解释：</strong>
最大差值出现在 i = 1 且 j = 2 时，nums[j] - nums[i] = 5 - 1 = 4 。
注意，尽管 i = 1 且 j = 0 时 ，nums[j] - nums[i] = 7 - 1 = 6 &gt; 4 ，但 i &gt; j 不满足题面要求，所以 6 不是有效的答案。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>nums = [9,4,3,2]
<strong>输出：</strong>-1
<strong>解释：</strong>
不存在同时满足 i &lt; j 和 nums[i] &lt; nums[j] 这两个条件的 i, j 组合。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>nums = [<em><strong>1</strong></em>,5,2,<em><strong>10</strong></em>]
<strong>输出：</strong>9
<strong>解释：</strong>
最大差值出现在 i = 0 且 j = 3 时，nums[j] - nums[i] = 10 - 1 = 9 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>2 &lt;= n &lt;= 1000</code></li>
	<li><code>1 &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 0 ms

```java
class Solution {
    public int maximumDifference(int[] nums) {
        int left=0;
        int right=1;
        int max=-1;
        while(right<nums.length){
            if(nums[left]<nums[right]){
                max = Math.max(max,nums[right]-nums[left]);
            }else{
                left=right;
            }
            right++;
        }
        return max;
    }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/maximum-difference-between-increasing-elements/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/maximum-difference-between-increasing-elements/description/)

Solution: [LeetCode](https://leetcode.com/articles/maximum-difference-between-increasing-elements/)  /  [LeetCode中国](https://leetcode-cn.com/articles/maximum-difference-between-increasing-elements/)

[回到目录](../README.md)