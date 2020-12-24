# 75. sort-colors | 颜色分类

## Question description

<!--If you want to use the English description, use <p>Given an array <code>nums</code> with <code>n</code> objects colored red, white, or blue, sort them <strong><a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank">in-place</a>&nbsp;</strong>so that objects of the same color are adjacent, with the colors in the order red, white, and blue.</p>

<p>Here, we will use the integers <code>0</code>, <code>1</code>, and <code>2</code> to represent the color red, white, and blue respectively.</p>

<p><strong>Follow up:</strong></p>

<ul>
	<li>Could you&nbsp;solve this problem without using&nbsp;the library&#39;s sort function?</li>
	<li>Could you come up with a&nbsp;one-pass algorithm using only <code>O(1)</code> constant space?</li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [2,0,2,1,1,0]
<strong>Output:</strong> [0,0,1,1,2,2]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [2,0,1]
<strong>Output:</strong> [0,1,2]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> [0]
</pre><p><strong>Example 4:</strong></p>
<pre><strong>Input:</strong> nums = [1]
<strong>Output:</strong> [1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 &lt;= n &lt;= 300</code></li>
	<li><code>nums[i]</code> is <code>0</code>, <code>1</code>, or <code>2</code>.</li>
</ul>
 instead-->
<p>给定一个包含红色、白色和蓝色，一共 <code>n</code><em> </em>个元素的数组，<strong><a href="https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95" target="_blank">原地</a></strong>对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。</p>

<p>此题中，我们使用整数 <code>0</code>、 <code>1</code> 和 <code>2</code> 分别表示红色、白色和蓝色。</p>

<p> </p>

<p><strong>进阶：</strong></p>

<ul>
	<li>你可以不使用代码库中的排序函数来解决这道题吗？</li>
	<li>你能想出一个仅使用常数空间的一趟扫描算法吗？</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>nums = [2,0,2,1,1,0]
<strong>输出：</strong>[0,0,1,1,2,2]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>nums = [2,0,1]
<strong>输出：</strong>[0,1,2]
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>nums = [0]
<strong>输出：</strong>[0]
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>nums = [1]
<strong>输出：</strong>[1]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 <= n <= 300</code></li>
	<li><code>nums[i]</code> 为 <code>0</code>、<code>1</code> 或 <code>2</code></li>
</ul>




## Solution

Language: **java**  /  Runtime: 1 ms

```java
class Solution {
  /*
  荷兰三色旗问题解
  */
  public void sortColors(int[] nums) {
    // 对于所有 idx < i : nums[idx < i] = 0
    // j是当前考虑元素的下标
    int p0 = 0, curr = 0;
    // 对于所有 idx > k : nums[idx > k] = 2
    int p2 = nums.length - 1;

    int tmp;
    while (curr <= p2) {
      if (nums[curr] == 0) {
        // 交换第 p0个和第curr个元素
        // i++，j++
        tmp = nums[p0];
        nums[p0++] = nums[curr];
        nums[curr++] = tmp;
      }
      else if (nums[curr] == 2) {
        // 交换第k个和第curr个元素
        // p2--
        tmp = nums[curr];
        nums[curr] = nums[p2];
        nums[p2--] = tmp;
      }
      else curr++;
    }
  }
}


```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/sort-colors/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/sort-colors/description/)

Solution: [LeetCode](https://leetcode.com/articles/sort-colors/)  /  [LeetCode中国](https://leetcode-cn.com/articles/sort-colors/)

[回到目录](../README.md)