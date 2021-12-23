# 1985. find-the-kth-largest-integer-in-the-array | 找出数组中的第 K 大整数

## Question description

<!--If you want to use the English description, use <p>You are given an array of strings <code>nums</code> and an integer <code>k</code>. Each string in <code>nums</code> represents an integer without leading zeros.</p>

<p>Return <em>the string that represents the </em><code>k<sup>th</sup></code><em><strong> largest integer</strong> in </em><code>nums</code>.</p>

<p><strong>Note</strong>: Duplicate numbers should be counted distinctly. For example, if <code>nums</code> is <code>[&quot;1&quot;,&quot;2&quot;,&quot;2&quot;]</code>, <code>&quot;2&quot;</code> is the first largest integer, <code>&quot;2&quot;</code> is the second-largest integer, and <code>&quot;1&quot;</code> is the third-largest integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [&quot;3&quot;,&quot;6&quot;,&quot;7&quot;,&quot;10&quot;], k = 4
<strong>Output:</strong> &quot;3&quot;
<strong>Explanation:</strong>
The numbers in nums sorted in non-decreasing order are [&quot;3&quot;,&quot;6&quot;,&quot;7&quot;,&quot;10&quot;].
The 4<sup>th</sup> largest integer in nums is &quot;3&quot;.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [&quot;2&quot;,&quot;21&quot;,&quot;12&quot;,&quot;1&quot;], k = 3
<strong>Output:</strong> &quot;2&quot;
<strong>Explanation:</strong>
The numbers in nums sorted in non-decreasing order are [&quot;1&quot;,&quot;2&quot;,&quot;12&quot;,&quot;21&quot;].
The 3<sup>rd</sup> largest integer in nums is &quot;2&quot;.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> nums = [&quot;0&quot;,&quot;0&quot;], k = 2
<strong>Output:</strong> &quot;0&quot;
<strong>Explanation:</strong>
The numbers in nums sorted in non-decreasing order are [&quot;0&quot;,&quot;0&quot;].
The 2<sup>nd</sup> largest integer in nums is &quot;0&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i].length &lt;= 100</code></li>
	<li><code>nums[i]</code> consists of only digits.</li>
	<li><code>nums[i]</code> will not have any leading zeros.</li>
</ul>
 instead-->
<p>给你一个字符串数组 <code>nums</code> 和一个整数 <code>k</code> 。<code>nums</code> 中的每个字符串都表示一个不含前导零的整数。</p>

<p>返回 <code>nums</code> 中表示第 <code>k</code> 大整数的字符串。</p>

<p><strong>注意：</strong>重复的数字在统计时会视为不同元素考虑。例如，如果 <code>nums</code> 是 <code>["1","2","2"]</code>，那么 <code>"2"</code> 是最大的整数，<code>"2"</code> 是第二大的整数，<code>"1"</code> 是第三大的整数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = ["3","6","7","10"], k = 4
<strong>输出：</strong>"3"
<strong>解释：</strong>
nums 中的数字按非递减顺序排列为 ["3","6","7","10"]
其中第 4 大整数是 "3"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = ["2","21","12","1"], k = 3
<strong>输出：</strong>"2"
<strong>解释：</strong>
nums 中的数字按非递减顺序排列为 ["1","2","12","21"]
其中第 3 大整数是 "2"
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = ["0","0"], k = 2
<strong>输出：</strong>"0"
<strong>解释：</strong>
nums 中的数字按非递减顺序排列为 ["0","0"]
其中第 2 大整数是 "0"
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= nums[i].length &lt;= 100</code></li>
	<li><code>nums[i]</code> 仅由数字组成</li>
	<li><code>nums[i]</code> 不含任何前导零</li>
</ul>




## Solution

Language: **java**  /  Runtime: 17 ms

```java
class Solution {
  public String kthLargestNumber(String[] nums, int k) {
    Arrays.sort(nums, (o1, o2) -> o1.length() == o2.length() ? o1.compareTo(o2) : o1.length() - o2.length());
    return nums[nums.length - k];
  }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-the-kth-largest-integer-in-the-array/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-the-kth-largest-integer-in-the-array/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-the-kth-largest-integer-in-the-array/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-the-kth-largest-integer-in-the-array/)

[回到目录](../README.md)